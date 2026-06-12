---
title: "&quot;Desktop effects could not be enabled&quot; - Gutsy"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by jacensolo on 2007-11-29
I have it working on my desktop but can't get it working on my laptop. I don't know what the specs are on my laptop besides having 512 mb of ram because it was given to me; I think it was made somewhere between 02-04, it's a Tobisha satellite. When I run the Compiz command I get this:  > Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 


I have the restricted drivers installed. When I run it it starts going but then stops. Does this mean I don't have enough memory to run it? If so, is there a way to slim compiz-fusion to make it work?

Thanks in advanced! :)

---

### Post by eg0n on 2007-11-29
Someone had exactly the same memory problem like you :) Take a look here   [http://ubuntuforums.org/showthread.php?t=626146](http://ubuntuforums.org/showthread.php?t=626146)

---

### Post by Bheegerji on 2007-11-29
> **jacensolo said:**
> I have it working on my desktop but can't get it working on my laptop. 

Can u tell me how got it working in ur desktop? I'm not able to enable "Extra" or "Normal" Visual Effects in Appearance Preferences for desktop. "The composite extension is not available" is what I get when I try to apply "Extra" visual effects. What is this composite extension? I use a 15" VGA monitor and a restricted video driver.

---

### Post by jacensolo on 2007-11-29
> **Bheegerji said:**
> Can u tell me how got it working in ur desktop? I'm not able to enable "Extra" or "Normal" Visual Effects in Appearance Preferences for desktop. "The composite extension is not available" is what I get when I try to apply "Extra" visual effects. What is this composite extension? I use a 15" VGA monitor and a restricted video driver.

I have 7.04 (feisty?) and forgot how i did it.

---

### Post by jacensolo on 2007-11-29
> **eg0n said:**
> Someone had exactly the same memory problem like you :) Take a look here   [http://ubuntuforums.org/showthread.php?t=626146](http://ubuntuforums.org/showthread.php?t=626146)

Xserver-xgl search doesn't turn up anything in synaptic.


Edit: I found it somehow.

---

### Post by jacensolo on 2007-11-29
I now have it on normal but I don't get the cube or wobbly windows. There is transparency in windows I'm not using though.

I turned on extra effects and now have wobbly windows, but still no cube :(.

---

### Post by Takster on 2007-11-29
> **jacensolo said:**
> I now have it on normal but I don't get the cube or wobbly windows. There is transparency in windows I'm not using though.

I turned on extra effects and now have wobbly windows, but still no cube :(.

> glxgears

in terminal. does that work first of all?

if it does, enable desktop cube plugin and make sure is is set to 4 sides. Oh and rotate cube plugin etc...

---

### Post by jacensolo on 2007-11-29
> **Takster said:**
> in terminal. does that work first of all?

if it does, enable desktop cube plugin and make sure is is set to 4 sides. Oh and rotate cube plugin etc...

Yes and how do I enable?

Edit: Google is my friend :)

---

### Post by Takster on 2007-11-29
> **jacensolo said:**
> Yes and how do I enable?

Edit: Google is my friend :)

Google is our overlord. :)

---

### Post by Bheegerji on 2007-12-02
Hey, I got my problem solved. Check [this]("http://ubuntuforums.org/showthread.php?t=628540&page=1").

Hope you find a solution soon.

---

