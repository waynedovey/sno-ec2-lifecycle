Single Node OpenShift lifecycle 

Run the Playbooks for the Instance. 

Ensure you replace the Instance ID and region

---
  vars:
    instance_id: "i-xxxx"
---
        region: "ap-xxx-x"

# Shutdown the EC2 Instance every night
00 19 * * 1-5 ansible-playbook /root/SNO/sno-ec2-shutdown.yaml >> /var/log/ansible-cron.log 2>&1

# Start the EC2 Instance only During the week
0 8 * * 1-5 ansible-playbook /root/SNO/sno-ec2-start.yaml >> /var/log/ansible-cron.log 2>&1
