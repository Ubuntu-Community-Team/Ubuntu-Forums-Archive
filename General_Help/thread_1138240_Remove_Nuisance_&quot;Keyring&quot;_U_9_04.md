---
title: "Remove Nuisance &quot;Keyring&quot; U 9_04"
date: 2009-04-26
forum: General Help
---

### Post by Vaedrah on 2009-04-26
In U 8_10 "keyrings" where introduced. I installed U 9_04 and the pesky "keyring" input occurs - how can this nonsense be killed?

I read one suggestion (of many)

Go to Applications/Accessories/Passwords and Encryption Keys

No this isn't a solution - didn't work.

I have no need for "keyrings" if others want "keyrings" then fine - but how do I eliminate this unwanted sillyness?

Thanks - in advance.

---

### Post by nortexoid on 2009-04-26
I'm curious about this as well. Whenever I start my desktop it asks me for my keyring password to connect to my wireless router. I wish it didn't.

---

### Post by spiderbatdad on 2009-04-26
I assume the problem is you are using a secured wireless network, and it is nm-applet requiring you to unlock the keyring everytime you boot and try to login to the network. See here:
[http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php](http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php)
or here:[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

---

### Post by ddrichardson on 2009-04-26
> **spiderbatdad said:**
> I assume the problem is you are using a secured wireless network, and it is nm-applet requiring you to unlock the keyring everytime you boot and try to login to the network. See here:
[http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php](http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php)
or here:[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)
Or just click the second one unless you want to visit Lifehacker first ;-)

---

### Post by spiderbatdad on 2009-04-26
> **ddrichardson said:**
> or just click the second one unless you want to visit lifehacker first ;-)

:p

---

### Post by geirha on 2009-04-26
Got this on my netbook too. Went to Accessories-> Passwords and Encryption Keys, removed the key from the default keyring, and set the login-keyring to default. Next time I logged in, I typed in the wireless password again, it got saved in the login-keyring, and I don't need to enter any password during login anymore.

---

### Post by nortexoid on 2009-04-26
> **spiderbatdad said:**
> I assume the problem is you are using a secured wireless network, and it is nm-applet requiring you to unlock the keyring everytime you boot and try to login to the network. See here:
[http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php](http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php)
or here:[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

I tried this and it farked my system. It gave me a repeated "Authentication Failed" dialog box that would just keep popping up at login every time I clicked ok. I had boot to console and re-edit the file, removing the line I had entered.

I wonder why it didn't work. My user password and keyring password are the same too. Hmm...

---

### Post by spiderbatdad on 2009-04-26
hmm.```
this only works if your keyring pw is the same as your login pw. if it isnt,
** before doing any of this** just delete your keyring -

```sorry for your woes, and glad you recovered. I'll probably not recommend that procedure again.

---

### Post by lisati on 2009-04-26
> **Vaedrah said:**
> In U 8_10 "keyrings" where introduced. 

Minor correction: keyrings have been around longer. I used it on 7.04 but had to do a little bit of setup myself.

---

