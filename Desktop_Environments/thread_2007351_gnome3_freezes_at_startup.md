---
title: "gnome3 freezes at startup"
date: 2012-06-20
forum: Desktop Environments
---

### Post by evilheart on 2012-06-20
i installed  gnome3 recently , along with cairo dock , 

now gnome sometimes freezes at the startup  , the mouse pointer is moving , but nothing gives response , not the panel or cairo dock , 

i have a Dell N5110 , with intel and nvidia graphic cards , and bumblebee installed , so the nvidia card is disabled by default.

any ideas what can be the source of the problem?

---

### Post by Frogs Hair on 2012-06-20
All the Ubuntu desktop shells run on top of Gnome 3 in 12.04. Are you referring to the Gnome Shell or Classic ?

---

### Post by evilheart on 2012-06-21
yes , it's gnome shell

---

### Post by Frogs Hair on 2012-06-21
Cairo Dock has open GL and the normal session. I have used it with a Nvidia graphics without card but know little about bumblebee.

I would suggest using the normal session and wait for a user that knows more about bumblebee.

I have not installed a dock with the Gnome Shell but have used the Cairo Dock stand alone desktop  session with 12.04 without any problem.

---

### Post by evilheart on 2012-06-22
thanks for the help :)

---

### Post by dmj99 on 2012-06-24
Think I have the same problem.  I installed the Gnome 3 shell on top of a new installation of Ubuntu 12.04. At startup, mouse moves but no windows open (when I hit activities, etc).  Have to hit the reset button. This seems to happen randomly.  Usually resetting will get me in.  BTW, really like the Gnome shell. . .more polished look and feel than unity.  DJ

---

### Post by rusty725 on 2012-06-29
same problem here tried different nvidia drivers + different kernels. gnome 3.4.1 randomly freezes. Ubuntu Devs can you shed some light on this issue ? It's been a while since ubuntu 12.04 came out and all I see is some lame updates in the update manager. I thought it was LTS release for crying out loud.

---

### Post by 0c-bill on 2012-09-05
I have the same problem. When logging into the Gnome 3 desktop shell; the session seems to freeze, except the pointer will move.

I think I read a post somewhere that claimed it had to do with some other service not being ready in time and so it would wait infinitely in the middle of starting up.

BUT I have found a better way to deal with it than restarting the computer. In my 12.04 installation, anyway:

ctrl+alt+f4 (or f1,2,3,etc...) into another terminal. 

Log in with an administrative account.

Then execute "sudo service lightdm restart".

This allows me to avoid an actual reset of the machine.  

When the lightdm service restarts it will actually switch my session back to tty7, which is where the desktop session usually resides on my machine.  So, you still have to go back to the other tty (ctrl+alt+f4 or f1,2,3...), and "exit" out of it sometime before you shutdown your machine.

Hope that helps somebody. :)

---

### Post by bluheron1 on 2012-09-05
I've also been having the same problem. Gnome Shell freezes and only the mouse pointer is active, nothing else loads. If I login in as soon as lightdm loads, the system freezes. If I wait a few seconds after lightdm loads, before logging in, Gnome Shell  doesn't freeze and everything works fine.

---

### Post by rusty725 on 2012-10-02
well I still get lockups even with gnome  shell 3.4.2. so far didn't find any solution. somebody please help

---

### Post by keegandoig on 2012-11-01
> **rusty725 said:**
> well I still get lockups even with gnome  shell 3.4.2. so far didn't find any solution. somebody please help

I had the same problem with the Gnome shell. I fixed it by logging into a Unity session, removing the Gnome shell and its configuration files by running

```
sudo apt-get purge gnome-shell 
```

This removes your Gnome tweak tool as well. Re-install by running
```
sudo apt-get install gnome-shell gnome-tweak-tool
```

Hope this fixes your problem.

---

### Post by aeronutt on 2012-11-18
Mine freezes about 1 in 10 times also (loggin in using gnome-shell). Frustrating.

---

