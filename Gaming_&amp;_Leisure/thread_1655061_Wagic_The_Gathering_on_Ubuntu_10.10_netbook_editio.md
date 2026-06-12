---
title: "Wagic: The Gathering on Ubuntu 10.10 netbook edition"
date: 2010-12-29
forum: Gaming &amp; Leisure
---

### Post by kraddark on 2010-12-29
Good Day! I am a new ubuntu linux user. I have an emachines em350 netbook with the 10.10 netbook edition. I was wondering how would I play this Magic: The Gathering homebrew from [http://wololo.net/wagic/download/]("http://wololo.net/wagic/download/"). Please Help Me Out.. Thanks!:confused:

---

### Post by davesalyers on 2010-12-29
I am using 10/04 LTS but I am in the same boat myself as I would also like to install Wagic (I am trying to install the alternate wagic.qt.14.1 edition with mouse support). I am a newbie when it comes to this.

If someone could help us, this may be a great way to help get me "over the hump" in Ubuntu skills in software installation beyond the Software Center and Synaptic (and installing classic DOS games to use with DOSBox - I got that down).

Thanks!

Dave

---

### Post by kraddark on 2011-01-01
still no response.. :cry:

---

### Post by TomPurnell on 2011-06-30
Installing Wagic on 11:04 64bit:

[Download Wagic]("http://wololo.net/wagic/download/") for Linux and extract zip.

(64 bit only) download 32bit libgif (I used [http://pkgs.org/debian-lenny/debian-main-i386/libgif4_4.1.6-6_i386.deb.html](http://pkgs.org/debian-lenny/debian-main-i386/libgif4_4.1.6-6_i386.deb.html) ) and extract to /usr/lib32/

Download libfmod 3.75 from [http://www.rpmfind.net/linux/rpm2html/search.php?query=libfmod-3.75.so](http://www.rpmfind.net/linux/rpm2html/search.php?query=libfmod-3.75.so) and extract the contents of ./usr/lib to /usr/lib/ (of if you're using 64bit, download the 32bit version and extract to /usr/lib32)

Make wagic executable (in your wagic folder, find wagic.qt or wagic.x11 and right click, properties, permissios, tick 'allow executing as a program', or chmod +x wagic.x11 from the command line)

Run the game with wagic.qt or wagic.x11

Should work for your netbook editions too

---

### Post by davesalyers on 2011-07-24
After doing a bit of online research, I found a couple of homebrew MTG (Magic the Gathering) games which allow for 1 player mode with computer AI that work just fine on Ubuntu: Magarena and Forge. Magarena has the more polished look and solid AI - it has about 900 cards in its library. Forge has almost 9000 cards and a decent AI. These are both written in Java so all you have to do is create a directory for them, download and extract to that directory, and run using Java. Just remember the first time you start the game up you should download the card graphics (this is one of the commands from within the program itself).

And I also recommend the Elements TCG online which is web-based and free. While it is a different game than MTG, it is well-balanced, very similar in tone to MTG, and runs fine through Firefox on Ubuntu.

---

