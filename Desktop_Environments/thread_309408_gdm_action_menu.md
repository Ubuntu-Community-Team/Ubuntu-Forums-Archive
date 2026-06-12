---
title: "gdm action menu"
date: 2006-11-29
forum: Desktop Environments
---

### Post by dlehman on 2006-11-29
I have saw a few posts about people wanting to either disable or to find the shutdown and restart buttons in Gnome and many times the solution is 

Login window and check show action buttons

my understating would be that would affect only the gdm login screen and not the user menu, but it affects the user menu.  

I am a former gentoo user and I never used gdm I logged in at console and typed 

```
startx 
```

so I don't know this may have been the same in gentoo but I looked in system monitor and it show the gdm process running as root and I looked at gdm.conf and it tell gdm to run as 
user=gdm
group=gdm

so I logged out and went to console and did

```
sudo killall gdm
```

then
```
startx
```

and now I have no shutdown or restart buttons 

I tried add myself to the gdm group but that did not bring the buttons back.  

is this a potential security risk to have gdm run as root or is this normal 

my goal is to allow some users to shutdown and restart but one not to.  and it has to be easy not 

```
sudo shutdown -r now 
```

I got my mom using ubuntu and she needs to be able to shutdown or restart when she wants
I have a 4 yr old that I setup an account for that is locked down with alacarte and pessulus so he has access to child's play gcompris and tuxpaint, because sometimes he just clicks and doesn't know what he is clicking and shuts down and things 

so I want to removes those options on his account 

should gdm be running as the user gdm, also xorg runs as root as well is there some way to configure permissions and groups to do this

Thank you

---

### Post by ingo on 2006-12-01
> ingo@ibm:~$ ps aux|grep kdm
root      4757  0.0  0.2   2736   340 ?        Ss   Nov30   0:00 /usr/bin/kdm
ingo     12119  4.0  0.5   2896   828 pts/4    R+   11:42   0:00 grep kdm
ingo@ibm:~$

that should answer your question as to whether root runs g/kdm.

as for buttons, I'm not sure which ones you are referring to, but a simple de- and reinstall should do the trick.

---

