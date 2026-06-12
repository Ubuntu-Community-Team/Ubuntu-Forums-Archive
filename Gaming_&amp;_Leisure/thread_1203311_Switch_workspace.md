---
title: "Switch workspace"
date: 2009-07-03
forum: Gaming &amp; Leisure
---

### Post by john17 on 2009-07-03
Hi,

please advise if it is possible to switch workspace when "World of Goo" is running on Jaunty

---

### Post by Bölvaður on 2009-07-03
if you are in windowed mode you can

---

### Post by john17 on 2009-07-03
Sorry to appear thick but what is windowed mode and how do I get into it

Many thanks

John

---

### Post by john17 on 2009-07-03
OK  I have found ALT + ENTER gives access to windowed mode. Next question, can I alter the screen size of this window somehow?

Thanks again

John

---

### Post by Bölvaður on 2009-07-03
according to their forums you can either get some tool to change the config or (what I would recommend) do it manually.

find ~/.wordofgoo  (might be different name of the directory) and find the config file. It should be clear what to change.
This is a hidden directory (with a dot in fron to the name) so you will need to press ctrl+H to find it.

---

### Post by john17 on 2009-07-03
Thanks Bölvaður

unfortunately my deb file did not create a config.txt so I found this solution 

make a config.txt file in ~/.WorldOfGoo and put something like:

<config>

<param name="language" value="en"/>
<param name="screen_width" value="1400"/>
<param name="screen_height" value="800"/>
<param name="ui_inset" value="10"/>

</config>

If it loads in full screen switch to windowed mode with ALT + ENTER

Thanks again for your help

John

---

