---
title: "&quot;Desktop effects could not be enabled&quot; after installation of new drivers."
date: 2009-04-11
forum: General Help
---

### Post by Danger Fox on 2009-04-11
I know there are other threads about this, and I see the one below mine with a similar problem, but mine is slightly different. My effects were working up until I installed the latest updates. So I then reinstalled the latest 64 bit nvidia drivers to fix this. They are now installed and activated, but whenever I try to enable desktop effects I get the error: "Desktop effects could not be enabled". My graphics card is a Nvidia 9800 GT if that helps. I can provide any additional information needed. Any help is appreciated.

---

### Post by schmidtbag on 2009-04-11
well first of all, are you even running 64 bit linux?  because you may have just installed the wrong thing.

also, are other 3d apps working?

---

### Post by Danger Fox on 2009-04-11
> **schmidtbag said:**
> well first of all, are you even running 64 bit linux?  because you may have just installed the wrong thing.

also, are other 3d apps working?

Haha, yes I am running 64 bit Linux. Could you give some examples of other 3d apps that would be running, because I'm not quite sure what you mean by that.

---

### Post by schmidtbag on 2009-04-11
like an application with 3d graphics.  if you kept the pack of games that ubuntu comes with, try the chess game and set it to 3d, thats how i test if 3d is working ok.

you should try installing more packages of it from synaptic like cssm and the extra plugins.  also try running "compiz --replace" in terminal and see if that helps, if not, tell us what it says.

---

### Post by Danger Fox on 2009-04-11
Ok, when I tried to run chess in 3D I got this error:
"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support".

Also when I ran "compiz --replace" I got this:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by schmidtbag on 2009-04-11
ya you definitely have no 3d support.

open up "Hardware Drivers" in administration and check which driver is activated.  if none are, activate one of them.  if the latest one is activated, switch to the previous one.

---

### Post by Danger Fox on 2009-04-11
When I open up hardware drivers and try to activate the previous one (177), I get an error after it stalls on the "Downloading and Installing" bar for a while. Is there any other way to install/activate this driver?

---

### Post by schmidtbag on 2009-04-11
try again, sometimes its glitchy but there is another way to install it.  open up synaptic, search for "nvidia-177-modaliases", "nvidia-177-kernel-source", and "nvidia-glx-177"

---

### Post by Danger Fox on 2009-04-12
Ok, I just tried that and after trying to get it to work afteer 3 or 4 tries, it still get the same error.

---

### Post by schmidtbag on 2009-04-12
are the 180 drivers uninstalled? you don't want to remove the modaliases of it but the other 2 packages should be removed.  try booting up into an earlier kernel too and see if that makes a difference.  i've had a very similar issue to you.  if all else fails you could try downloading the setup from nvidia's site.

---

