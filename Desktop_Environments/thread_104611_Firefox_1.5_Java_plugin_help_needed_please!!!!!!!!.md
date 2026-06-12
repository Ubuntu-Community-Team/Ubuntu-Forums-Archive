---
title: "Firefox 1.5 Java plugin help needed please!!!!!!!!!!!!!!"
date: 2005-12-16
forum: Desktop Environments
---

### Post by shaj on 2005-12-16
Hi All.

My first time posting here. I did do a search before posting. So please forgive me if I missed out on a possible solution.

Just installed Firefox 1.5 Manually. Installed The Firefox plugins & Java itself using Automatix. No luck with Java. It keeps sayin I'm missin the plugin.

So I used the automated script available to Install Firefox 1.5

Still no luck. Tried everything. It keeps sayin I'm missin the Java plugin!!!

What am I doing wrong??? :(

---

### Post by hod139 on 2005-12-16
Did you have the java plugin working before, with the older version of firefox?
This link: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) has a section on setting up plugins.  Hopefully the answer is in there.

---

### Post by Leif on 2005-12-16
if you don't have java installed, take a look here for a howto on both firefox and java : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by shaj on 2005-12-16
Ok Guys...now I am totally confused.

I just 'kinda' figured out the problem.

I seem to have multiple installations of Firefox 1.5

I'm not sure how many, but I know there's a minimum of 2.

I have one in my Home directory!!! I'm not sure if the automated script installed it there :(

I made a link to libjavaplugin in the 'home' folder install's plugin folder and the Java test ran fine. But when I open up Firefox using the main link on the gnome toolbar, the Java doesn't work. I have no idea where that Installation is :(

I'm really a linux newbie. Can u guys help me find 'all' installations I have of Firefox 1.5 on my system and uninstall them all so I can start a fresh Install? I hope you guys can help. Appreciate it. thanks.

---

### Post by fog on 2005-12-16
Try this:
> sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

---

### Post by shaj on 2005-12-16
[QUOTE=fog]Try this:[/QUOTE]


tried it...says file already exists...I really don't understand this...

any ideas on how to see how many installations of Firefox I have n uninstall it?

---

### Post by syklitengutt on 2005-12-17
the one in your home directory is safe tu delete I think.
Just where the unpacking is going.

The one in usr/lib is the real one I think.

(did you use the install FF1.5 script?)
if so, im shure because I have the same problems. Cant get my java to vork,
but all other plugins is working just fine...

Need My unibet... godammit....
So now im n a pent no mghz spesified and 64 mg ram and win95...
Takes 15 min to start the unibet poker client....

---

### Post by DrLaban on 2005-12-17
I got the same problem. 
Java is installed and working fine. Firefox 1.5 installed and working fine.
I have created the symlink, but firefox still says that I am missing the plugin.

?????

---

### Post by DrLaban on 2005-12-17
I Solved it :D
These command did the trick:

 > cd /opt/firefox/plugins/
 sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

---

