---
title: "Gutsy Compiz-Fusion Effects"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by amtur_poet on 2008-02-19
I just installed gutsy on my dell desktop computer, and installed compiz-fusion settings manager. However, when I go to activate desktop effects, it gives me the error message "Desktop Effects Could Not Be Enabled". I have an Intel Graphics Chipset, but Desktop effects work on my laptop with gutsy, and it has the same graphics chip. What can I do to get desktop effects working?

---

### Post by bvav22 on 2008-02-19
you probably need to enable composite extensions


edit xorg...

sudo nano /etx/X11/xorg.conf


at the bottom you will see composite extension, set it to "1"


then save and it should work

---

### Post by amtur_poet on 2008-02-19
All that shows up is a blank file in the terminal.

---

### Post by alsamman on 2008-02-19
> **bvav22 said:**
> you probably need to enable composite extensions


edit xorg...

sudo nano /etx/X11/xorg.conf


at the bottom you will see composite extension, set it to "1"


then save and it should work

what he meant to say was: sudo nano /etc/X11/xorg.conf

---

### Post by Kubotaz4 on 2008-02-20
I get the same response as amtur_poet, about getting the blank document.  I looked around the etc file and my file name for xorg is xorg.conf.1 I am also having effect issues with my comp.  I dont know how to install the latest ati driver once Ive downloaded it.  Ive tried the sudo sh ati... but came back with cannot find file.  help please!

---

### Post by amtur_poet on 2008-02-20
I can't find compisite extentions in the xorg file. Should I add it in?

---

### Post by theduffman on 2008-02-20
ive enabled composite, after getting the composite not available error.. and now get
Desktop effects could not be enabled

what do i have to do to get ATI drivers to work with this thing.. Ubuntu`s are fine, but i wanna play games too...

---

### Post by amtur_poet on 2008-02-20
Where do I find composite extensions in xorg?

---

### Post by amtur_poet on 2008-02-26
I just found out that my computer is 64-bit, not 32-bit. I think that changes things. Also, when I run the command "compiz" in the terminal, I get this output:

> Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity 


---

### Post by Crafty Kisses on 2008-02-26
> **amtur_poet said:**
> I just found out that my computer is 64-bit, not 32-bit. I think that changes things. Also, when I run the command "compiz" in the terminal, I get this output:

Sounds like some of your hardware is Blacklisted.

---

### Post by amtur_poet on 2008-02-26
Yeah, but what can I do to get around that, or fix it?

---

