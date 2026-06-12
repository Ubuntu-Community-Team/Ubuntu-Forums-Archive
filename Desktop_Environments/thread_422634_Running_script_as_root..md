---
title: "Running script as root."
date: 2007-04-25
forum: Desktop Environments
---

### Post by JSHN on 2007-04-25
Hi everyone!

Got a little problem someone might have an answer to.

I have been starting to script some functions in Linux I don't want to start directly at boot,
but now I would really love if there is some way to make the scripts run as root without
enter the password every time? Now when I'm booting my box and when the script is about to start after entering x-server the terminal asking for the root password every time.

Like when I'm about to connect to my WLAN in the script, the dhclient needs to be executed as root, so the script cannot run without password input.

Is there anyway to bypass this?? I might be totally wrong by can you add a keyring or somthing to the script?

---

### Post by az on 2007-04-25
You can grant fine-grained rights to specific commands using sudo.  You can use the NOPASSWORD option in the suco configuration.  I believe it's detailed in the sudo manpage.

You can also change the privs of the file to be onewed by root and suid so that it always runs as root.

---

### Post by JSHN on 2007-04-25
Ok! I will try this as soon as I get home.

Thanks!

---

### Post by JSHN on 2007-04-25
I tried this but I'm kinda new to Linux and cannot get it to work.

Can you give me an example on how to do this???

---

### Post by az on 2007-04-26
[http://ubuntuforums.org/showpost.php?p=140756&postcount=8](http://ubuntuforums.org/showpost.php?p=140756&postcount=8)

---

### Post by bashologist on 2007-04-26
Edit: Nvm, read his question wrong.

---

