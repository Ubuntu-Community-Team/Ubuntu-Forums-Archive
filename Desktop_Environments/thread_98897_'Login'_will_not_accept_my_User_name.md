---
title: "'Login' will not accept my User name"
date: 2005-12-04
forum: Desktop Environments
---

### Post by L Campbell on 2005-12-04
I have been playing around with my Kubuntu, attempting to get online with ‘dial-up’ but still not there yet, so I decided to reload the program, in case that would help.

After the program was loaded, my ‘login’ failed.  I had written down the User name and Password I used, so I thought I might have mis-typed it but I couldn’t get anything to work.

Once more I loaded the program, using the same name and password.  This time I am absolutely sure I typed what I intended to type but I am still getting ‘login failed’.

I used a four letter User name and a two letter Password.  This is information that I have used successfully in the past.

Is there something I can do to get logged in, without have to re-load again?

Thanks.

---

### Post by atoponce on 2005-12-04
Download and burn a Knoppix disc, throw it into the CDROM and reboot.  Mount your harddrive, pull up a terminal, and type:

```
sudo passwd <login>
```

This will reset the password for the user that you created.  Reboot, and you should be fixed.  I am just shooting from the hip here, and it does feel like I'm missing something, but I can't put my finger on it...

---

### Post by L Campbell on 2005-12-04
[QUOTE=atoponce]Download and burn a Knoppix disc, throw it into the CDROM and reboot.  Mount your harddrive, pull up a terminal, and type:

```
sudo passwd <login>
```

This will reset the password for the user that you created.  Reboot, and you should be fixed.  I am just shooting from the hip here, and it does feel like I'm missing something, but I can't put my finger on it...[/QUOTE]

Hi, thanks for your reply, I appreciate it.

I entered just what you showed here and got the message
 
      bash: syntax error near unexpected token 'newline'

When I tried it using my password (for passwd) and my login name (for login) I still got the same error message.

Kind regards.

---

### Post by metoo on 2005-12-05
on grub, select recovery, then on the console do a
apt-get -f install
or
apt-get install --reinstall kubuntu-desktop

(kubuntu CD in the drive)

---

