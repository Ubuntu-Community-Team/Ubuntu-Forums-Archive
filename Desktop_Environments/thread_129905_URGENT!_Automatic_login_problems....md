---
title: "URGENT! Automatic login problems..."
date: 2006-02-14
forum: Desktop Environments
---

### Post by Postman on 2006-02-14
I tried having my computer automatically log me in since I'm the only user for this computer.  When I came back from work, the computer was shut down (suspiciously) and I booted up the computer and it tried automatically logging me on but it gave me this: "Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  Files s(h)ould be owned by user and have 644 permissions."  So it sends me back to the login screen, I type my login and password and it says the same thing about the '$HOME/.dmrc', gives me a brown screen and sends me back to the login screen.  The only way I've been able to get on the Internet is that I run through the console and use firefox.  First, what did I do to cause this to happen?  I only have been trying to automatically log me in when I boot and trying to install my Lexmark Z55 drivers.  Second, what can I do to fix this?  Hopefully, it's not too severe.  Please help out cuz I am a novice at using console language so if I need to do stuff through there, please give me all details.  Thanks guys.

Matt T.

---

### Post by stevea1210 on 2006-02-14
I did a quick search for .dmrc and got this

[http://ubuntuforums.org/showthread.php?t=91455]("http://ubuntuforums.org/showthread.php?t=91455")

---

### Post by Postman on 2006-02-15
Well I tried using the "sudo chown (username) /.dmrc" "sudo chmod 644 .dmrc" and "sudo chmod 755 /home/(username)"  It only gave me error messages that were mentioned in the linked post about the same problem.  Is there any other suggestions on what I should try?  Thanks.

Matt T.

---

