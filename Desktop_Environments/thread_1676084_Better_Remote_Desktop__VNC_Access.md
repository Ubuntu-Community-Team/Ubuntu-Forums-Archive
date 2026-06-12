---
title: "Better Remote Desktop / VNC Access?"
date: 2011-01-26
forum: Desktop Environments
---

### Post by photographicd on 2011-01-26
So I'm setting up this Kiosk machine and I'm having Ubuntu automatically log in under the kiosk user.  I would like to be able to remotely manage it so I turn on the Ubuntu Remote Desktop feature with a password and specify that the user should not be asked when I connect.  Problem is: It sucks.

The kiosk _must_ auto login.  But When I try to connect via VNC it prompts the kiosk user for the keyring password.. This is obviously not going to work.

Question: Can I get a plain old, It-just-works, remote desktop / VNC service to run on Ubuntu that will show me the main desktop?  OR is there a way to fix the remote desktop so that it doesn't ask for the keyring without compromising the security of the kiosk?


PS:  I've tried other options like nomachine but these seem to give you a fresh remote desktop instead of displaying the REAL main desktop window that the kiosk user sees.  Not what i'm looking for.

Thanks a lot!

---

### Post by Krytarik on 2011-01-26
I use x11vnc for remote access since a couple of years, with the following command at the server:
```
x11vnc -display :0 -rfbauth .vnc/passwd
```
You have to store a password before with:
```
x11vnc -storepasswd PASSWORD FILE
```
[http://manpages.ubuntu.com/manpages/maverick/man1/x11vnc.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/x11vnc.1.html)

No user at the server is needed to accept the connection or do anything about it, but the main problem is that after the connection is terminated, the command has to be run again at the server to allow a new connection.

About the keyring: I don't know much about it, but since the keyring with the login password is opened at the automatic login, wouldn't it be possible to somehow include the password for the remote connection in that keyring?

---

### Post by krunge on 2011-01-27
> **Krytarik said:**
> 
No user at the server is needed to accept the connection or do anything about it, but the main problem is that after the connection is terminated, the command has to be run again at the server to allow a new connection.

Add the option "-forever" to the x11vnc command line to have it keep listening for more connects after the first viewer disconnects.

Possibly related: To have more than one simultaneous viewer connection add the option "-shared".

---

### Post by Krytarik on 2011-01-27
> **krunge said:**
> Add the option "-forever" to the x11vnc command line to have it keep listening for more connects after the first viewer disconnects.

Possibly related: To have more than one simultaneous viewer connection add the option "-shared".
Great, thanks for posting those options! I could have searched for it before, but never really needed it.

I'm proud to have the developer himself here (if I'm guessing right)!! :-)

---

### Post by Krytarik on 2011-01-31
Today I came across those 'guide' to disable the password query in your original setup. But you have of course to consider the somewhat lower security in this scenario.
[http://ubuntuforums.org/showpost.php?p=10211581&postcount=3](http://ubuntuforums.org/showpost.php?p=10211581&postcount=3)

---

