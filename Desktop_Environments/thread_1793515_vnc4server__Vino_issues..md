---
title: "vnc4server / Vino issues."
date: 2011-06-29
forum: Desktop Environments
---

### Post by Zerauskire on 2011-06-29
Ok. From the beginning... 

I use vnc4server and it used to work great. After I updated to Natty though, now it doesn't allow me to drag and drop. I have it set up to tunnel through SSH using putty and RealVNC viewer on my Windows laptop. This is the way I have always done it and it has worked just fine.

After searching around for a solution to this I gave up and decided to just go with Vino since it's standard in Ubuntu anyways. This however has opened up a new issue for me. It won't connect at all using Vino. 

I opened up the Remote Desktop Preferences window and selected the following settings.

**Sharing:**
"Allow other users to view your desktop" [COLOR="red"]Checked[/COLOR]
"Allow other users to control your desktop" [COLOR="red"]Checked[/COLOR]

**Security:**
"You must confirm each access to this machine" [COLOR="Red"]Unchecked[/COLOR]
"Require the user to enter this password:" [COLOR="Red"]Unchecked (for now)[/COLOR]
"Configure network automatically to accept connections" [COLOR="red"]Tried both checked and unchecked[/COLOR]

It says "Your desktop is only reachable over the local network. Others can access your computer using the address localhost." which is fine because when i'm tunneling I connect using localhost:5900 anyways.

Now when I go back to using vnc4viewer with localhost:5901 it still connects just fine. I've also tried disabling vnc4server while attempting to use Vino. Nothing has worked so far.

So basically, here's what i'm looking for. I don't mind sticking with vnc4server if someone can help me resolve the drag and drop issue but if anyone can tell me what i'm doing wrong with my Vino config that will be a viable solution as well.

---

### Post by Zerauskire on 2011-06-30
Well I found the following posts but i'm not really sure what to do with it. I can't find the file that the second link is referring to.

[https://bugzilla.gnome.org/show_bug.cgi?id=620240](https://bugzilla.gnome.org/show_bug.cgi?id=620240)

[http://git.gnome.org/browse/gtk+/commit/?id=0efb24f589a74c4a4e78a1803d6e7205be9c1984](http://git.gnome.org/browse/gtk+/commit/?id=0efb24f589a74c4a4e78a1803d6e7205be9c1984)

---

### Post by Zerauskire on 2011-07-05
Installed TightVNCserver and still have the same issue. So since they both utilize the same config I suppose it's something to do with that.

Still never got Vino to work either. It connects and then immediatly disconnects me like as if i'm putting in the wrong password but it does that even if I don't use a password.

---

### Post by Zerauskire on 2011-07-05
I guess this is a known bug for quite some time now. Odd that this being the fact that no one replied here. This forum seems to become more and more useless day by day. I see threads go without replies over and over again.

Regardless, anyone interested. Here's the link to the information regarding this known bug.

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/587856](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/587856)

---

