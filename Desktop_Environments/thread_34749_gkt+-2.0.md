---
title: "gkt+-2.0"
date: 2005-05-16
forum: Desktop Environments
---

### Post by EndersGame on 2005-05-16
OK, I'm sure this is something simple.

I'm trying to build mozilla sunbird and I'm getting an error saying:

checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I can find gtk2 packages in Synaptic, and since I'm running the default Gnome desktop, I'm assuming this stuff should be there.  Can someone tell me how I can make pkg-config find it?

Thanks.

---

### Post by Maestro23 on 2005-05-16
[QUOTE=EndersGame]OK, I'm sure this is something simple.

I'm trying to build mozilla sunbird and I'm getting an error saying:

checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I can find gtk2 packages in Synaptic, and since I'm running the default Gnome desktop, I'm assuming this stuff should be there.  Can someone tell me how I can make pkg-config find it?

Thanks.[/QUOTE]


Just went into Synaptic, the gtk-stuff is in there.  Did you add all the repositories to your /etc/pat/sources.list file per the Ubuntu guide?  If not, the link to the guide is in my sig.  Hope that helps ya...

---

### Post by EndersGame on 2005-05-16
[QUOTE=Maestro23]Just went into Synaptic, the gtk-stuff is in there.  Did you add all the repositories to your /etc/pat/sources.list file per the Ubuntu guide?  If not, the link to the guide is in my sig.  Hope that helps ya...[/QUOTE]

My problem (I think) is that I have all the gtk packages, etc, but pkg-config isn't finding them properly, either because they are named differently or for some other reason.  So, as far as I know, the repositories won't help me there.

---

### Post by ow50 on 2005-05-16
You need the dev package libgtk2.0-dev.

---

### Post by EndersGame on 2005-05-17
[QUOTE=ow50]You need the dev package libgtk2.0-dev.[/QUOTE]

This requires libpango1.0-dev, which isn't in any of the standard repositories I've added. Any idea where I might find it?

---

### Post by ow50 on 2005-05-17
[QUOTE=EndersGame]This requires libpango1.0-dev, which isn't in any of the standard repositories I've added. Any idea where I might find it?[/QUOTE]
It's in Hoary's main repository, the very same where libgtk2.0-dev is. I don't know how you managed to find one but not the other.

---

### Post by EndersGame on 2005-05-17
[QUOTE=ow50]It's in Hoary's main repository, the very same where libgtk2.0-dev is. I don't know how you managed to find one but not the other.[/QUOTE]
 Hmm...whadya know, there it is.  Must have just been an synaptic glitch that it couldn't find it.  Thanks for all the help!

---

### Post by EndersGame on 2005-05-19
ow50, Thanks again for all your help.  I've managed to get through the next few hurdles in this process, but now I'm stuck on:

configure: error:  Could not find the following X libraries:  -lXt

Any idea what I should do to get those libraries in there?

(I apologize for morphing this question.  I can create a new post if you prefer.)

---

### Post by ow50 on 2005-05-19
[QUOTE=EndersGame]configure: error:  Could not find the following X libraries:  -lXt

Any idea what I should do to get those libraries in there?[/QUOTE]
My best guess would be that you need libxt-dev and libxt6.

---

### Post by EndersGame on 2005-05-19
[QUOTE=ow50]My best guess would be that you need libxt-dev and libxt6.[/QUOTE]
 Brilliant!  It worked and has finally started building. :-)  Thanks again!

---

