---
title: "Dead keys in Breezy"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Wes24 on 2005-10-17
Hi,

Breezy is great, but one things keeps annoying me: I cannot get dead keys to work. I'm Dutch, so everytime I write something, the piece is loaded with spelling errors. If I enable the keyboard layout US international with dead keys, it still doesn't work (in Hoary it worked). 

Does anybody know how to get the dead keys to work? Thanks in advance.

---

### Post by gonr on 2005-10-19
I had similar problems, and judging from the boards here so did other people.

I think its an unsolved bug, but I found that installing this package fixed things.
[http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb](http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb)

---

### Post by kairu0 on 2005-11-05
[QUOTE=gonr]
I think its an unsolved bug, but I found that installing this package fixed things.
[http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb](http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb)[/QUOTE]

I tried that and I still don't have dead keys in Kubuntu :(

---

### Post by dj_thom on 2005-11-12
You should uncheck the 'Both Alt keys together change group' box in System > Preferences > Keyboard > Layout Options > Group Shift/Lock Behaviour

After that Alt Gr + 5 or e results in &#8364;, and " followed by e results in &#235;.

---

### Post by teaker1s on 2005-11-12
for properly dead keys "wilki multimedia keys" will in effect remap the whole keyboard thats how I made my keyboard work as all keys are mapped and you can change everyone around

---

### Post by mikko.ohtamaa on 2005-11-16
It's a bug. See [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372)

What worked for me:

Terminal command "setxkbmap fi" sets Finnish layout correctly. Use it with your keyboard map code (no idea what it is)

---

