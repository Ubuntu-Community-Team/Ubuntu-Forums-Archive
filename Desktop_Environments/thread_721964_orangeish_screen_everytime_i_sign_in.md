---
title: "orangeish screen everytime i sign in"
date: 2008-03-11
forum: Desktop Environments
---

### Post by quequeque2 on 2008-03-11
every time i sign in theres an orangeish screen for about 10-20 seconds and then i can see my desktop.

i was wondering if it is normal on ubuntu or if i can fix it

---

### Post by dark_phantom on 2008-03-12
I see it too.

---

### Post by BlowflyBob on 2008-03-12
I have not tested this, but a quick google lead me to this solution:

```
sudo gedit /etc/gdm/PreSession/Default
```

Head to the very bottom of the file and find this (around line 61):
```

# Default value
 if [ "x$BACKCOLOR" = "x" ]; then
 	BACKCOLOR="#dab082"
 fi

```

And change the hex value for the color to whatever you want it to be.

Oh, and the [thread it came from](http://www.linuxquestions.org/questions/ubuntu-63/what-is-this-screen-between-boot-and-desktop-614297/).

---

### Post by quequeque2 on 2008-03-12
when i find
# Default value
 if [ "x$BACKCOLOR" = "x" ]; then
 	BACKCOLOR="#dab082"
 fi
i didnt have to change anything, it is already written and it is the same thing
i dont think that this is what i should do...

---

### Post by dummyhead3 on 2008-03-14
You have no choice about this... all you can do is change it's color...

---

