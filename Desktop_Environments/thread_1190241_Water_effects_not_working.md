---
title: "Water effects not working"
date: 2009-06-17
forum: Desktop Environments
---

### Post by Tholley on 2009-06-17
I just installed compiz config-settings-manager the other day on my 9.04 and so far all is working well except the Water Effects. I re-did the bindings again as the were set already, I believe ctrl-super (super = winkey right?). I hold them down and left click on the mouse and all it does is creat a box like as if I wasn't holding the keys down.
 
Fire works fine by holding the shift-super, and I even swapped keys with Water and still wouldn't work. Ctrl-alt will let me move the cube around with no problem.
 
 
 
also if you could tell me how to make it rain.
 
Thanks!

---

### Post by Tholley on 2009-06-18
I have tried on 2 seperate computers, and it will not work on either. Is there a plugin I'm missing?
 
bump...

---

### Post by ~sHyLoCk~ on 2009-06-18
Did you check if the key bindings are not repeated?

---

### Post by notbad on 2010-01-03
not working for me, the rain and others work exept with mouse. 8400gs card. can somebody help?

---

### Post by fishkid257936 on 2010-07-24
I know this is old, but can someone help us?

---

### Post by iSeizmik on 2010-07-24
I don't want to be patronising, but did you check the 'Enable Water Effect' box?

---

### Post by fishkid257936 on 2010-07-24
yes...

---

### Post by howefield on 2010-07-24
> **fishkid257936 said:**
> I know this is old, but can someone help us?

Not all graphics cards work with the water effect.

What is the output of these terminal commands..

```
lspci | grep VGA
```

```
glxinfo | grep GL_ARB_fragment
```

---

### Post by fishkid257936 on 2010-07-24
lspci | grep VGA: 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

glxinfo | grep GL_ARB_fragment: nothing

---

### Post by howefield on 2010-07-24
> **fishkid257936 said:**
> lspci | grep VGA: 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

An oldie but goldie...

> glxinfo | grep GL_ARB_fragment: nothing

No output means your graphic card isn't up to the task of enabling the water effects.

Hard lines, you need a better card if you want the magic of the water ;-)

---

