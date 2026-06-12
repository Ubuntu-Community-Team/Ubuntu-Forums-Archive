---
title: "Problem with new Hostname"
date: 2005-12-29
forum: General Help
---

### Post by theoldsausage on 2005-12-29
Ok, a few days ago i installed the newest ubuntu on my laptop and everything was fine until i got a little ambitious and now i'm having some problems. when i first set it up i set up the host name(not sure if thats what it's called) i let the installer call it ubuntu, as it was there by default. I did not see any problem with this so i went for it. everything installed fine and a few days later i decided to change the name from ubuntu to default. when i did this i started getting messages telling me that GNOME will not run properly now. so i go to change it back and i cannot. the network admin pannel will not come up, nor will the user permissions pannel. i also tried to edit the hostname file to read what it did before and it was read only so i was not able to change it. i also could not change the files permissions which is odd because i'm the system admin.

EDIT: i now know that i have to be in the root account to do this. i tryed logging in to the root account but could not. When i try to specify my password with the "sudo password root" command in i get the message "unable to lookup default via gethostbyname () "   

can someone please help me here. i have no idea what else i can do to fix this thing.

thanks.

---

### Post by 23meg on 2005-12-29
Please post the contents of your /etc/hosts file.

---

### Post by queenorych on 2005-12-29
Not sure what you changed.  If memory serves me to change the hostname you must change it in /etc/sysconfig/network and in /etc/hosts.  /etc/sendmail may also need to be changed, as well as /etc/smb/smb.conf.

You problem is probably just a missing /etc/hosts entry for your new hostname.

---

### Post by theoldsausage on 2005-12-30
[QUOTE=queenorych]
You problem is probably just a missing /etc/hosts entry for your new hostname.[/QUOTE]

Yea, that was the problem. Thanks.

---

### Post by bigtexjc42 on 2005-12-30
same problem - I know that I need to revise the file names while in Recovery Mode, but once at the text-prompt in Recovery mode, I have no idea how to edit the file /etc/hosts.

I feel like I want to type 'edlin' from my old DOS 2.0 days!!!

How do I edit this file?

---

### Post by Jammy_Stuff on 2005-12-30
```
gedit /path/to/file
```

For that file you may need

```
sudo gedit /path/to/file
```

---

### Post by sciurus on 2005-12-31
*sudo nano /path/to/file* doesn't require you to leave the console. Running a GUI as root always makes me nervous.

---

