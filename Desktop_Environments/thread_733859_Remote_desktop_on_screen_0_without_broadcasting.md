---
title: "Remote desktop on screen 0 without broadcasting"
date: 2008-03-24
forum: Desktop Environments
---

### Post by wangrui on 2008-03-24
Hi guys,

I have been using remote desktop for quite a long time. There is something kept bothering me.

The problem looks like this:

I have a desktop computer installed ubuntu. I will use the desktop computer most of the times. But sometime I need to access my desktop in the meeting room. I can't use the ubuntu's remote desktop. Because it use screen 0. If I connect to my desktop using VNC, my physical computer will also be activated, and the screen will show exactly like what's on VNC. I have to kept my physical computer log out. Because there will always be someone in front of my computer when I'm not at seat. It's kind a bad feeling to show others what I'm doing by the physical screen like broadcasting. If I lock the screen from VNC, the physical screen will also locked. If I unlock the screen, the physical screen will also be unlocked. Other people in front of my computer will see everything I'm doing.

So normally I use a separate VNC server using another screen. But I have to close all applications on screen 0 to use remote desktop. Because some application (a lot of the office softwares) can only run on one screen each time. If I want to use screen 1, I have to close all applications on screen 0, if I want to switch back, I have to do the same thing again. It's very bothering sometime.

When I was using redhat, I would start another VNC server. And run all application on that VNC server. And use vncviewer to do my work no matter on local machine or remotely. Which means, I always use VNCViewer even I'm using the physical machine. I will use screen 0 to start a VNCViewer to access screen 1. But this don't seems works on ubuntu. When I open another VNCServer on ubuntu, the desktop looks very weired, all of my gnome setting is gone. But I didn't see any problem in VNC log. I will try again tomorrow if I find time.

I'm thinking maybe I got everything wrong. Maybe there is a decent solution for this problem. Can anybody help me out? Is there any way to access the deskop remotely without broadcasting everything on the physical screen? Thank you.

---

### Post by sir_blargh on 2008-03-24
Have you considered using XDMCP?  I don't know much about it, but it'll allow you to remotely connect to a machine and be greeted with a new graphical login prompt.  Obviously you'll login and then launch whatever applications you need (no clue if the specific software you mention will allow it to also operate in this environment) and none of the actions will show up on the machine you've connected to.  

[This ]("http://ubuntuforums.org/showpost.php?p=3568096&postcount=14")post gives details pertaining to enabling XDMCP.  Note that you need restart GDM after enabling remote graphical logins and also you need to install xnest on the computer you're connecting with.  If the computer you're connecting with is another ubuntu machine, you can use the terminal server client and select xdmcp as the protocol, but if it's a windows machine, something like Exceed should do the trick.

But hey, maybe there's some option in the vnc server that says "don't actually display this on the connected computer" but I don't know of one! :)

---

### Post by wangrui on 2008-03-25
Thank you. But I need a more secured method. And I'm one of those guys who prefer not to try new thing if the current one still can work.

I did another testing today. It seems if I login into gnome before starting the VNC server, everything will be wrong. But if I start the VNC server using text tty before the GDM login. Then everything will works.

I guess I will stick to VNC server. Now I will always have the VNC server started in boot sequence. And only use the default gnome session to start the vncviewer. Wonder if there is a way that I can start the vncviewer directly from console. Because having two desktop running on the same machine still can got conflicted.

---

### Post by daflame on 2008-03-25
Use FreeNX, you get a separate desktop that is unseen unless you log in and you can suspend and resume sessions if you want to all encrypted in an SSH tunnel automatically.  Also, you can access as many physical or virtual desktops as you want with VNC shadowing.  Plus, its rendering of the screens is nearly like being at the station. (Not the VNC mirroring)  Not to mention being able to send files back and forth to your local machine via Samba/Windows File Sharing.  The instructions are in the link below.

---

### Post by wangrui on 2008-04-07
I found out how to use VNC server on both ubuntu 7 and 8. The original problem is caused by gnome-settings-daemon. By the following way it can be solved:

type gconf-editor, follow the path /apps/gnome_settings_daemon/plugins/keyboard and unselect the "active" checkbox. After that the vnc server can run without any problem.

---

### Post by RC Howe on 2008-04-22
```
$ ssh -X *ip address or hostname*
``` Works as well. You'll get a terminal, and when you launch a graphical application from it it will show up on your laptop screen, but not on your desktop. You have to be running a *nix with X11, though :). Oh, and make sure your usernames on both machines are the same, otherwise you will need ```
ssh -X *username*@*ip address or hostname*
```

If you don't have ssh installed, sudo apt-get install ssh or installing from synaptic would be the way to do it.

It's faster than VNC as well.

---

