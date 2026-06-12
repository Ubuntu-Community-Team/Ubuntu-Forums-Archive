---
title: "Shutdown problem with fast-user-switch-applet Karmic"
date: 2009-11-15
forum: Desktop Environments
---

### Post by linuxus95 on 2009-11-15
Hi, and many thanks for all replies. I am running Karmic and I appear to have a very weird problem with shutting down the computer. I use GNOME, and when I use the fast user switch applet and press the shutdown button, I am prompted to enter a password of an admin user, becuase other users are apparently logged on to the computer. No other users are, or have been, logged on since the boot up of the computer. For me, this is not a great issue, as I am an adminitsrator, but it is a problem for other regular users using the computer, as they cannot shutdown without either logging off first, or holding the power button. I know it is a small problem, but it is still kind of annoying. Once again, thanks for any replies!:D

---

### Post by roro986 on 2010-02-18
> **linuxus95 said:**
> Hi, and many thanks for all replies. I am running Karmic and I appear to have a very weird problem with shutting down the computer. I use GNOME, and when I use the fast user switch applet and press the shutdown button, I am prompted to enter a password of an admin user, because other users are apparently logged on to the computer. No other users are, or have been, logged on since the boot up of the computer. For me, this is not a great issue, as I am an administrator, but it is a problem for other regular users using the computer, as they cannot shutdown without either logging off first, or holding the power button. I know it is a small problem, but it is still kind of annoying. Once again, thanks for any replies!:D

I currently have a very similar problem. I think it was produced when I was logged into this machine with ssh and samba and press cancel in the multiple users logged in dialog when trying to shutdown the machine in a hurry.

The problem now persist and every time (even when I have no network and only 1 user logged in) the multiple user dialog appear when I try to shutdown the machine.

Have anyone find the solution for this? I would really like to keep my home folder and installation intact.

---

### Post by roro986 on 2010-02-18
> **roro986 said:**
> I currently have a very similar problem. I think it was produced when I was logged into this machine with ssh and samba and press cancel in the multiple users logged in dialog when trying to shutdown the machine in a hurry.

The problem now persist and every time (even when I have no network and only 1 user logged in) the multiple user dialog appear when I try to shutdown the machine.

Have anyone find the solution for this? I would really like to keep my home folder and installation intact.

After some digging around I find a ugly way to fix this problem.
The ugly fix is to edit  the file '/usr/share/polkit-1/actions/org.freedesktop.consolekit.policy' and change the value between <allow_active></allow_active> to yes. This will disable the multiple users logged in dialog.

Finally it should show something like this

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

I don't know what package causes the problem so I think I cannot fill a bug for this.


Anyone have had more luck with this? I really don't like this fix

---

