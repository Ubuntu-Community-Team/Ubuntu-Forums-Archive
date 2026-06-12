---
title: "Root privileges on KDE"
date: 2005-03-31
forum: Desktop Environments
---

### Post by andradelipe on 2005-03-31
Friends,

Many tasks in KDE asks for root passord, i've made one with "sudo passwd", so, in terminal, I can use it, but, on KDE... I'm trying to adjust my clock, trying to adjust my SMB preferences "witch Kde Control Center" and if I put my user passwd, nothing happens, else if i try root passwd, KDE says that is icorrect. question:

1 - How to enable root login on Kubuntu?
2 - How to have those configurations privileges on Kubuntu, like in gnome warty, that you just have to put your user passwd to configure things... ?

---

### Post by lao_V on 2005-03-31
[QUOTE=andradelipe]

1 - How to enable root login on Kubuntu?
[/QUOTE]

in terminal: sudo passwd root

---

### Post by andradelipe on 2005-03-31
[QUOTE=lao_V]in terminal: sudo passwd root[/QUOTE]

I've did it, but is not what i want now, I want to login in KDE graphical mode (kdm) with Root...

---

### Post by lao_V on 2005-03-31
[QUOTE=andradelipe]I've did it, but is not what i want now, I want to login in KDE graphical mode (kdm) with Root...[/QUOTE]

ahhh...haven't anyone told you not to login to any DM using the root account? bad bad things could happen :-)

have a look in kcontrol -> login manager..you might need to enable root login from there?

---

### Post by andradelipe on 2005-03-31
This is not working, because I'm on my user account, and don't have privileges to access this feature, like many other ones. 
Nothing relationed to Root privileges work, and the su passwd created doesn't work in graphical mode. I just want to configure things in KDE, where do I can have Root privileges to do this?

---

### Post by irf on 2005-03-31
[QUOTE=andradelipe]F
1 - How to enable root login on Kubuntu?[/QUOTE]
you need to edit your kdmrc file, changing "AllowRootLogin=false" to "AllowRootLogin=true"
not sure where ubuntu installs KDE, as i've never used ubuntu, you could try under:
/usr/kde/3.4/share/config/kdm/kdmrc
change 3.4 in the above path to your version of KDE.
The file you want to edit is kdmrc.
HTH
PS it's not a good idea to run KDE as root

---

### Post by m29389 on 2005-03-31
When kde asks for the root password it is using sudo behind the scenes so just type in your user password (same thing when you want to use kdesu to run something).  I read something on the kubuntu web site about this, saying that they know it isn't clear and was something that would get sorted.

You say this doesn't work for you though so I don't know.  Has your password got non alphanumeric characters in it?  I ask this because the language settings seem a bit screwy in kubuntu so maybe you are using different keyboard layouts in different places.

---

### Post by andradelipe on 2005-03-31
I didin't use alphanumeric keys. The resolution by editing kdmrc works fine! I've made all the confs that was problems before, and back to my user account so happy!
Is true that have this problem with su on graphical mode, I hope this can be repaired soon. 
Good thanks!

---

### Post by xmorph on 2005-03-31
I have this same problem.

1. I enabled root passwd via sudo for terminal use.

2. When I try to use anything in KDE that requires admin rights *NEITHER* my root or my user password are valid.

---

### Post by uberlinux on 2005-04-06
THIS IS THE SOLUTION!

STEP 1.  sudo gedit /etc/kde3/kdm/kdmrc
STEP 2.  click the find button, enter "AllowRootLogin"
STEP 3.  change the value to "true"
STEP 4.  save, logout, log back in as ROOT!

_____.:BIG THANKS TO IRF!:.________

---

