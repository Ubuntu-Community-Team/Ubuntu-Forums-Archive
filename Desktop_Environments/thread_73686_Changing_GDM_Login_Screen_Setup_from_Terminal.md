---
title: "Changing GDM Login Screen Setup from Terminal"
date: 2005-10-09
forum: Desktop Environments
---

### Post by greymoose58 on 2005-10-09
Hi all,

The motherboard in our family computer is playing up so that it will not recognise the keyboard. Because it is the fastest machine we have I figured I'd set up a remote logon from another machine. 

I found the instructions at [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941) but without a keyboard I can't logon locally to change the Login Screen Setup (Step 1). 

Is there a way to change these settings from the terminal? I can SSH into the machine in question without any trouble.

Thanks in advance.

---

### Post by mlomker on 2005-10-09
Edit the /etc/gdm/gdm.conf file.  You'll find this:

```

[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false

```

Just change that to **true**.

---

### Post by greymoose58 on 2005-10-10
Thanks for that. It sorted out that problem. 

Now I'm getting a VNC authentication failed message when I enter the password.  I've been Googling for an answer and I finally figured out I should look in the log file. I  found this:

Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option

I'm lost - what setting? I tried a Google and adding --window-with-profile as an option. Can anyone point me in the right direction?

Thanks.

Phil.

---

### Post by mlomker on 2005-10-10
I've personally never set this up.  I ran across [this thread]("http://ubuntuforums.org/showthread.php?t=35429") and it seems relevant.

---

### Post by greymoose58 on 2005-10-10
Thanks for that. It is all greek to me. I'm still too much of a newbie to follow it. 

I've seen that Breezy is supposed to have easy terminal serving built in. I think I'l wait a couple of days and have a crack at that. :)

---

