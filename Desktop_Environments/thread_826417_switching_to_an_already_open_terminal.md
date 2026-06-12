---
title: "switching to an already open terminal"
date: 2008-06-11
forum: Desktop Environments
---

### Post by lpanebr on 2008-06-11
Hello,
I use compiz to open the terminal the size and place I want. Thats great but...

***Is there any way to set a keyboard shortcut to just switch to an already open terminal window?***

Thanks!!

---

### Post by sdennie on 2008-06-11
You should be able to do this fairly easily.  First:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

Then, go to System->Preferences->Advanced Desktop Settings->General Options->Commands.  Make one of the commands under the Commands section:

```

wmctrl -xa gnome-terminal

```

Add a corresponding hotkey in the Key Bindings section of that tab.

---

### Post by lpanebr on 2008-06-12
Thanks!!

I had just found another way using the Tilde app which is kind of cool cause it slides the terminal IN/OUT with the hotkey..

I tryed your suggested way with wmctrl and compiz and it also worked nicely. I believe I could add another command to make the terminal window get BELOW as to make it go away but it would have to be asecond hotkey right?

I am divided...  think will try both for while..  Tilda seems to work fine though... I have some focus issues at first (the terminal wouldnt came raised and focused), but after arranging the Tilda  and compiz settings I think is ok now..

but hey, THANKS again for the precise and fast reply!

---

### Post by lpanebr on 2008-06-12
well..   those issues I mentioned with Tilda are still happening. It apear to happen mostly when I am with focus on Firefox. The trerminal will slide but bellow it.. :(

---

### Post by sdennie on 2008-06-12
> **lpanebr said:**
> 
I tryed your suggested way with wmctrl and compiz and it also worked nicely. I believe I could add another command to make the terminal window get BELOW as to make it go away but it would have to be asecond hotkey right?


You could make a script to toggle between focused and minimized.  There are a lot of things you can do with wmctrl command.

> **lpanebr said:**
> well..   those issues I mentioned with Tilda are still happening. It apear to happen mostly when I am with focus on Firefox. The trerminal will slide but bellow it.. :(

That sounds like something you may be able to fix by going to System->Preferences->Advanced Desktop Effects->General Options->Focus & Raise Behavior.  Trying playing with Focus Prevention Level.

---

### Post by lpanebr on 2008-06-17
After some more googling around I learned that what I was looking for is called a QuakeTerminal (yes, after the one in the game....)
The script on [http://www.linuxjournal.com/article/9973](http://www.linuxjournal.com/article/9973) gave me what I needed and I changed it a bit so it also opens up the terminal in case it's not already opened..

here's the code:

```

#!/bin/sh

touchTerm()
{
        wmctrl -r 'Quake Terminal' -e '0,0,0,1279,500'
        wmctrl -r 'Quake Terminal' -b add,shaded
        wmctrl -r 'Quake Terminal' -b add,below
        touch /tmp/.quake.shaded
}

S1=`wmctrl -l|grep 'Quake Terminal'|wc -l`

if [ $S1 -eq '0' ]; then
    gnome-terminal --window-with-profile='Quake Terminal' --title='Quake Terminal'
    wmctrl -r 'Quake Terminal' -e '0,0,0,1279,500'
#    echo `wmctrl -l|grep 'Quake Terminal'|wc -l`
fi
# Unshade and bring to front
if [ -f /tmp/.quake.shaded ]; then
    wmctrl -r 'Quake Terminal' -b remove,below
    wmctrl -r 'Quake Terminal' -b remove,shaded
    wmctrl -a 'Quake Terminal'
    rm /tmp/.quake.shaded
# Shade and send to back
else
        touchTerm
fi

```

hope it be of use to other lost souls like me out there...  Quake Terminal.. who would've thought of that?

---

