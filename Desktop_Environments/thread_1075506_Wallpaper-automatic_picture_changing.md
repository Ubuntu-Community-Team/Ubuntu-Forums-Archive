---
title: "Wallpaper-automatic picture changing"
date: 2009-02-20
forum: Desktop Environments
---

### Post by nathand28 on 2009-02-20
I have setup an xml file to change the wallpaper after 10 seconds. This is my first time using xml, so it is just a test. I made a small png file, coloured it red and named it 1.png. I made a second file ,coloured it orange, and named it 2.png, and so on. The background is set to tile.

When the sequence reaches the 8th file, which is the last one, it displays for a few seconds, then changes to the solid colour set in the appearance preferences, which in my case, is white. About 10 seconds later it restarts the sequence.
I am wondering if it is possible have the 8th file display for 10 seconds, then restart, skipping the white screen.
Here is the xml file:

```

<background>
&#8722;
<static>
<duration>1.0</duration>
<file>/home/nathan/Desktop/Picture Test/1.png</file>
</static>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/1.png</from>
<to>/home/nathan/Desktop/Picture Test/2.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/2.png</from>
<to>/home/nathan/Desktop/Picture Test/3.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/3.png</from>
<to>/home/nathan/Desktop/Picture Test/4.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/4.png</from>
<to>/home/nathan/Desktop/Picture Test/5.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/5.png</from>
<to>/home/nathan/Desktop/Picture Test/6.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>~/Desktop/Picture Test/6.png</from>
<to>~/Desktop/Picture  Test/7.png</to>
</transition>
&#8722;
<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/7.png</from>
<to>/home/nathan/Desktop/Picture Test/8.png</to>
</transition>
&#8722;
<static>
<duration>0.0</duration>
<file>/home/nathan/Desktop/Picture Test/8.png</file>
</static>
</background>

```
_________________________________________________
Solved it, turned out that:
1. I hadn't made the script executable;
2. I had put in dir='pwd' instead of dir=`pwd`.

The install script is attached.

---

### Post by mcduck on 2009-02-20
Make sure you haven't got any errors in the XML file and that all files are named correctly. It shouldn't ever go to background color unless it's missing one of the files.

Also you'll probably want to set time for the last image to something higher than 0,0.
```

<background>

<static>
<duration>1.0</duration>
<file>/home/nathan/Desktop/Picture Test/1.png</file>
</static>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/1.png</from>
<to>/home/nathan/Desktop/Picture Test/2.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/2.png</from>
<to>/home/nathan/Desktop/Picture Test/3.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/3.png</from>
<to>/home/nathan/Desktop/Picture Test/4.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/4.png</from>
<to>/home/nathan/Desktop/Picture Test/5.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/5.png</from>
<to>/home/nathan/Desktop/Picture Test/6.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/6.png</from>
<to>/home/nathan/Desktop/Picture Test/7.png</to>
</transition>

<transition type="overlay">
<duration>10.0</duration>
<from>/home/nathan/Desktop/Picture Test/7.png</from>
<to>/home/nathan/Desktop/Picture Test/8.png</to>
</transition>

<static>
<duration>10.0</duration>
<file>/home/nathan/Desktop/Picture Test/8.png</file>
</static>

</background>
```

edit: there's also some issues with quick transitions, and very high CPU usage isn't the only one of them. If you wish to actually use animated wallpaper themes I recommend minimum transition times of 10 minutes (which seems to be the limit when CPU usage drops to reasonable levels).

---

### Post by nathand28 on 2009-02-20
Thanks Mcduck. It was a very stupid error, I only had 7 files, plus the xml file.

---

### Post by nathand28 on 2009-02-23
I've got that figured out, but how would I make an install script to change the paths to wherever the folder was?
Something like this:
```

dir=`pwd`

cat <<END_OF_XML > $xml
<background>

<static>
<duration>60.0</duration>
<file>$dir/1.png</file>
</static>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/1.png</from>
<to>$dir/2.png</to>
</transition>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/2.png</from>
<to>$dir/3.png</to>
</transition>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/3.png</from>
<to>$dir/4.png</to>
</transition>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/4.png</from>
<to>$dir/5.png</to>
</transition>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/5.png</from>
<to>$dir/6.png</to>
</transition>

<transition type="overlay">
<duration>60.0</duration>
<from>$dir/6.png</from>
<to>$dir/7.png</to>
</transition>

<static>
<duration>60.0</duration>
<file>$dir/7.png</file>
</static>

</background>

END_OF_XML

###END INSTALL SCRIPT

```

---

### Post by nathand28 on 2009-02-25
Bump

---

### Post by nathand28 on 2009-03-01
Bump

---

### Post by jjgomera on 2009-03-01
i cant help with script, but i think program feh do what you look for

---

### Post by nathand28 on 2009-03-01
Is the prgram called feh?

---

### Post by jjgomera on 2009-03-01
yes feh, it's in repo

---

### Post by nathand28 on 2009-03-01
Solved it, turned out that:
1. I haden't made the script executable;
2. I had put in dir='pwd' instead of dir=`pwd`.

---

