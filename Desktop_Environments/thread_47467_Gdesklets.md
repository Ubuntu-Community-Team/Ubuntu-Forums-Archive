---
title: "Gdesklets"
date: 2005-07-08
forum: Desktop Environments
---

### Post by profediego on 2005-07-08
Ok i managed to install gdesklets via synaptic, then download some desklets from their webpage install them and make them run.. ok so far.. but i want them to hace transparency support... so via sypnaptic i installl Xcompsite libs, restar and nothing their is no tranparency in my desklets... Cpuld somebody give me a hint here, thanks.

---

### Post by varunus on 2005-07-08
Follow the X compositing manager howto in the tips and tricks section.  You need to enable compositing in your xorg.conf and start the compositing manager, and also use the "transset" tool after doing this to set transparency.  The howto explains how to do this.

---

### Post by profediego on 2005-07-10
HI, i have read all the the how to tips and tricks and i couldnt find anything about composite or transset or how to enabled them..   

I search the forum and find some threads and follow the steps mention... i have already install xcompmanager and transset, modify my Xorg, 
with this

Make sure you have this somewhere in your xorg.conf:

Section "Extensions"
Option "Composite" "Enable"
EndSection

Also, if you are using the nvidia binary chipset driver, add these lines in your Section "Device":

Option "AllowGLXWithComposite" "true"
Option "RenderAccel" "true"

But so far i cannt enable the transparency option, does somebody have any ideas.

Thanks

---

### Post by AndyAWS on 2005-07-13
I've got gdesklets35.1 installed and lm-sensors but for 2 days I've been trying to access the gdesklets web page with no luck....does anyone know if they're down or moving to a new server?

Is [http://gdesklets.gnomedesktop.org](http://gdesklets.gnomedesktop.org) the correct url?

---

### Post by arrizaba on 2005-07-13
Once every two times that I try to connect to the gdesklets main page, it is not functional. The URL you say is the correct one. Try in some days....  :???: 
That's the thing I find most dissapointing with Gdesklets, the lack of mainteinance. I've turned to adesklets instead:

[HTML]http://adesklets.sourceforge.net/[/HTML] 

They have less desklets and is a bit more green that gdesklets, but it's a promising alternative.

---

### Post by pt123 on 2005-07-13
[QUOTE=arrizaba]
They have less desklets and is a bit more green that gdesklets, but it's a promising alternative.[/QUOTE]
They dont even have a screenshots section ](*,)  , it sure doesn't look promising.

---

### Post by arrizaba on 2005-07-14
Huh?

They do have a screenshot section in the forums. Take a look at:

[COLOR=Blue]http://adesklets.sourceforge.net/forum/viewtopic.php?t=2[/COLOR]

Adesklets is still on a early development phase, and is less popular than gdesklets, so it goes a bit slow. But, some of the desklets are nice (try yap, for instance, much better than the StarterBar of Gdesklets), and the webpage is always available.

---

### Post by pt123 on 2005-07-14
Wow you have to search to get screenshots thats ridiculous. Its should be one of the main sections on the homepage. Its scary to think these people are trying to make a desktop tool.

---

### Post by arrizaba on 2005-07-14
Well, read their main page:

------------------------------------------------------
[SIZE=2]Screenshots wanted![/SIZE]

So you have a pretty cool desktop, and you use adesklets? Share it with the world now! We hope to release a gallery of nicest screenshots soon. Will your desktop be part of it?
---------------------------------------------------------

So, the reason they do not have the screenshots on their page is because they haven't got many to show. The project is still in its infancy. But, I use both gdesklets and [COLOR=Blue]adesklets[/COLOR] and I am happier with [COLOR=Blue]adesklets[/COLOR]. 
If only we could use [COLOR=MediumTurquoise]SuperKaramba[/COLOR] in Gnome...., that would be it.

---

### Post by pt123 on 2005-07-14
When you are making a product you should always show how it looks. Thats just crap if they couldn't even take a screenshot, while they were testing it out.

---

