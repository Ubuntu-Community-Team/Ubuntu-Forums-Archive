---
title: "Change ownership of a file..."
date: 2011-09-16
forum: Desktop Environments
---

### Post by Moozillaaa on 2011-09-16
What's the command for this?

I brought up root access at the CLI, and the command below, but no luck...

chuck-04d0@chuck-04d0-laptop:~$ exec sudo -s
[sudo] password for chuck-04d0: 
root@chuck-04d0-laptop:~# chown -hR chuck-04d0 /home/chuck-04d0/Desktop/
root@chuck-04d0-laptop:~# chown -hR chuck-04d0 /home/chuck-04d0/Desktop/Barrel
root@chuck-04d0-laptop:~# chown -hR chuck-04d0 /home/chuck-04d0/Desktop/Barrel/*
root@chuck-04d0-laptop:~# chown -R chuck-04d0 /home/chuck-04d0/Desktop/Barrel/*
root@chuck-04d0-laptop:~# chown -R chuck-04d0 /home/chuck-04d0/Desktop/Barrel/
root@chuck-04d0-laptop:~# sudo chown -R chuck-04d0 /home/chuck-04d0/Desktop//Barrel/
root@chuck-04d0-laptop:~# sudo chown -R chuck-04d0 /home/chuck-04d0/Desktop/Barrel/*
root@chuck-04d0-laptop:~# sudo chown -R chuck-04d0 /home/chuck-04d0/Desktop/Barrel/011crop.jpg

Help?

---

