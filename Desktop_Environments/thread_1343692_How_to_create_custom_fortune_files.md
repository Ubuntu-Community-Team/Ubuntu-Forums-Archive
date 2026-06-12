---
title: "How to create custom fortune files?"
date: 2009-12-02
forum: Desktop Environments
---

### Post by qrwe on 2009-12-02
Hello,

I saw a very cute litte application called "Wanda the Fish", which is a GUI verision of command line program "fortune". Now, I would like to create my own fortune cookies, which can be found in /usr/share/games/fortunes, but found that together with the text file containing the text, theres a binary .dat file.
My question is: how do I create these .dat files in order to make my custom made fortunes? Searched the web but could only find manuals to fortune itself (which I've already read, hope I didn't miss something) or some pre-made files.
Thanks for any help!

---

### Post by Lars Noodén on 2009-12-02
The package [fortunes](http://packages.ubuntu.com/karmic/fortunes) is the one with the data.  Try grabbing the [source package](http://wiki.debian.org/apt-src) and poking around in that.  


Here is a somewhat old document that tells how to work with src packages:
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

### Post by qrwe on 2009-12-07
OK, thank you very much for your help and time, but the solution was (as usual) to read the manual once again, this time more carefully. As I couldn't google a howto, I hereby create one.

[SIZE="4"]HOWTO: create custom fortune cookies files[/SIZE]
[LIST=1]
[*]Open your favourite editor and add the strings that you want to be shown when running "fortune" in terminal. BE SURE to add a single line with a letter % in it, between every string.
[*]Save this file to whatever file name you want; this guide uses "yourlist" as example.
[*]When done adding strings, run the command "strfile -c % yourlist yourlist.dat". This will create a .dat file for your cookie file, which contains a header structure and a table of file offsets for each group of lines. This allows random access of the strings.
[*]Run "fortune yourlist" to eat the fruit of your work. That's it! :-)
[*]If you want this cookie file to appear as any other of the standard fortune cookies (when simply running "fortune"), just add your string file and .dat file into "/usr/share/games/fortunes/".
[*]Oh, and one more thing: if you want to change anything in "yourfile", you will need to repeat this HOWTO again for it to work.
[/LIST]

Good luck!

---

### Post by uriel1998 on 2011-02-19
Just wanted to say "Thanks" publicly for this.  I'd been searching for a while myself for exactly this reason - though I've been piping the output through cowsay instead.  :)

---

### Post by pasu11 on 2011-12-18
Thank you, qrwe! That's very helpful. I created my own custom fortunes in no time :)

---

### Post by nothingspecial on 2011-12-18
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

