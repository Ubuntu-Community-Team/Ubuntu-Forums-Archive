---
title: "HOWTO install Starcraft &amp; Broodwar (with battle.net) with cedega"
date: 2006-09-24
forum: Gaming &amp; Leisure
---

### Post by duality on 2006-09-24
I am on edgy, and by being able to install Starcraft and Broodwar, i am now free to delete my Windows partition (yey).

1. Install Cedega.
2. Install Starcraft on cedega
3. Install Broodwar on the Starcraft profile
4. Now, to make everything work on battle.net you must install MS Fonts:

sudo apt-get install msttcorefonts

4. Now to make a shortcut on your desktop, and because somtimes cedega runs slow, you must do the "nice" command:

echo "nice -n 19 cedega" >> ~/Desktop/cedega && sudo chmod +x ~/Desktop/cedega

I will break down this command to tell the ones that dont know what it does:
echo "nice -n 19 cedega"  (print to terminal "nice -n 19 cedega")
nice -n 19 cedega  (is the command that will be run to give higher priority to cedega, its what you would type in terminal)
>> ~/Desktop/cedega  (print the echoed text to a file called "cedega" that will be on the desktop)
&& ( and =) )
sudo chmod +x ~/Desktop/cedega ( makes the file executable )

There, now you can run starcraft (or any other games) with cedega at full speed by just clicking on the desktop shortcut.

And remember to leave the "FreeType and Xrender" option enabled in cedega on starcraft&broodwar options.

bye

---

