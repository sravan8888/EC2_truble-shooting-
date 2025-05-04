# EC2_truble-shooting-
1. EC2 Instance Not Reachable (SSH Not Working)
2. High CPU Usage on EC2
3. EC2 Instance Fails to Boot
4. Elastic IP Not Working
5. Disk Full Issue
6. EC2 Scheduled Events or Unexpected Reboot
7. Unable to Attach/Detach Volume
8. Application Not Accessible (Web App/Service Down)

   | 🔢 | Scenario / Issue                     | Possible Causes                                                | Quick Fix / Troubleshooting                                                                    |
| -- | ------------------------------------ | -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| 1  | **SSH Not Working**                  | SG/NACL blocking port 22, wrong key, no public IP, `sshd` down | ✔ Check SG, NACL rules <br> ✔ Verify key and IP <br> ✔ Use EC2 Serial Console or detach volume |
| 2  | **High CPU Usage**                   | App overload, insufficient instance type                       | ✔ Check CloudWatch <br> ✔ Use `top`, kill processes <br> ✔ Resize instance                     |
| 3  | **Instance Fails to Boot**           | Corrupt OS, startup script error                               | ✔ Check System Logs, Serial Console <br> ✔ Detach root volume, fix configs                     |
| 4  | **Elastic IP Not Working**           | Wrong ENI, route table issue                                   | ✔ Re-check EIP attachment <br> ✔ Ensure 0.0.0.0/0 → IGW <br> ✔ SG/NACL rules correct           |
| 5  | **Disk Full**                        | Log files, no monitoring                                       | ✔ Run `df -h`, `du -sh` <br> ✔ Clear logs/temp files <br> ✔ Expand EBS volume                  |
| 6  | **Unexpected Reboot/Stop**           | Maintenance event, app crash                                   | ✔ Check EC2 Events tab <br> ✔ View CloudTrail logs <br> ✔ Review system logs                   |
| 7  | **EBS Volume Attach/Detach Fails**   | Wrong AZ, volume in use                                        | ✔ Ensure same AZ <br> ✔ Unmount volume <br> ✔ Use `lsblk`, mount manually                      |
| 8  | **Web/App Not Loading**              | App not running, SG issue                                      | ✔ Check service status <br> ✔ Allow HTTP/HTTPS <br> ✔ Test with `curl localhost`               |
| 9  | **Instance Terminated Unexpectedly** | Spot instance interruption, automation                         | ✔ Review CloudTrail logs <br> ✔ Switch to On-Demand/Reserved                                   |
| 10 | **Can't Connect to RDS from EC2**    | SG not allowing traffic, DNS issue                             | ✔ RDS SG allows EC2 SG <br> ✔ Use correct hostname/port                                        |
