---
title: "The group could not be changed. You do not have the permissions necessary to change t"
date: 2009-04-30
forum: General Help
---

### Post by Su-27FlankerB on 2009-04-30
Hi I have UbuntuStudio 8.1 Intrepid Ibex for AMD64 installed.
I am unable to view the files in one of my hard drives.
Samsung 40GB EIDE strictly used for Data Storage only.
Filesystem is FAT32 or vFat.
I am trying to change the permissions of this drive but I get the message:
"The group could not be changed."
"You do not have the permissions necessary to change the group of "DATA DRIVE"."

I have tried adapting solutions from other posts but I can't seem to fix this.
Thanks in advance.

My 40GB HDD uses Fat32 and is labled DATA DRIVE.
Can anyone give me the exact commad to change the permissions of this drive so that all users can access it?

:confused:

---

### Post by jbrown96 on 2009-04-30
First, you will want to change the ownership to you.

```
sudo chown -R $USER:$USER /PATH/TO/MOUNT-POINT
```

Then change the permissions. Most people recommend the 777 permission, but I think that giving your files execute permissions is reckless. Try 666 instead.

```
sudo chmod -R 666 /PATH/TO/MOUNT-POINT
```

---

### Post by Su-27FlankerB on 2009-05-02
This OS is really ruining my day.
I never had this issue with Kubuntu 8.04.1 and Windows XP.

Here's a screenshot of what I did as per the advise of **jbrown96**.

[IMG]http://img22.imageshack.us/img22/4942/53175718.png[/IMG]

Maybe I'm doing it all wrong.
Above is an image of the error I get.
Thanks.

---

### Post by jbrown96 on 2009-05-02
Only the owner of a file/folder can change its permissions. Since you are not root, you are not allowed to change the permissions. You should be able to read/write the files though. Why did you make the owner root but make the group yours? If you enter that chown command earlier, it will fix everything.

---

### Post by Su-27FlankerB on 2009-05-03
> **jbrown96 said:**
> Why did you make the owner root but make the group yours?

I did not..
It was probably because the drive was installed after Ubuntu Studio was installed.
I used that drive as an external for some time until I got a 160GB drive that I decided to return it inside the CPU.

I've been trying the chown thing but no luck as of now.
May be I'm doing something wrong.
Am I?

:confused:

---

### Post by kayvortex on 2009-05-03
Well, first of all, could you post the contents of the file /etc/fstab since that file will tell the OS how to mount your drive, and so you wont need to go chmod-ing or chown-ing about.

Could you also, on a reboot (so that I can see what its default settings are), type
```
mount
```
on the terminal (no "sudo" required) so that I can check to see how it is, indeed, being mounted.

---

### Post by neu2buntu on 2009-05-03
heres a dangerous method to do this do code in terminal ```
gksu nautilus
``` and goto the permissions of your drive and change the settings, then close nautilus down ...

---

