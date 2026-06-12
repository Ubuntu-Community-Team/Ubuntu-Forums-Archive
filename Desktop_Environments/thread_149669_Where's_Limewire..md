---
title: "Where's Limewire."
date: 2006-03-24
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-03-24
I'm trying to install Limewire.

I'm following the wiki: [https://wiki.ubuntu.com/P2PHowTo?highlight=%28limewire%29](https://wiki.ubuntu.com/P2PHowTo?highlight=%28limewire%29)

At the first step, it's giving me a 404 Not Found error for the .zip file.

Any ideas?

---

### Post by Ubuntuud on 2006-03-24
Just take the official file from the limewire website, worked fine for me.
You could also try Frostwire...

---

### Post by taurus on 2006-03-24
I also recommand frostwire since it's open source and you don't have to see that annoying message about upgrading to pro version...  There is an Ubuntu version at [http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html).  So, download it and from a terminal, do
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```
Then, you can access it from Applications -> Internet -> FrostWire.

---

### Post by Edward The Bonobo on 2006-03-24
Thanks.

Does Frostwire have a big enough peer community to make it worthwile?

Limewire - on their site they have a .rpm.  Can someone remind me how to convert to a .deb, please?

But I see they also have a .zip under 'other' - and this includes Linux.  Is this .zip the same as the .zip on the Ubuntu wiki?

---

### Post by Edward The Bonobo on 2006-03-24
Hmm.  Downloaded and installed Frostwire.  It's right there in the menu, but nothing happens when I select.  Also...FrostWire - and case variants thereof - don't work in Terminal.

---

### Post by taurus on 2006-03-24
```

sudo alien <filename>.rpm
sudo dpkg -i <filename>.deb

```
What did you type from a terminal?  You need to use lower letter case in this case as
```

frostwire

```

---

### Post by Edward The Bonobo on 2006-03-27
Yes...I typed frostwire (and also Frostwire and FrostWire).  Nothing happened.

I'm extremely impressed by Limewire so far, though - compared with past experience of WinMX and KazaaLite.

---

### Post by Jason_25 on 2006-03-27
Looks like you might have installed frostwire via alien or the frostwire deb.  This can cause trouble. 

If you still want to use frostwire (it's open source and nicely laid out) then do this. Grab the tar.gz off the website and unzip it anywhere.  Then try running frostwire from the command line.  cd to Frostwire's lib folder and 
```

java -jar FrostWire.jar

```

---

### Post by billdd on 2006-03-29
Hi Guy had the same problem.  Try replacing this link with the link the instructions gave

 wget -c [http://www.limewire.com/LimeWireSoftOther](http://www.limewire.com/LimeWireSoftOther)

Hope this helps

Cya 
Bill

---

### Post by zerhacke on 2006-03-29
What, no gtk-gnutella suggestions yet?  Shame on you all!

```
sudo apt-get install gtk-gnutella
```

---

### Post by LanceM on 2006-03-29
If you are having problems with the .deb install of frostwire, check this out:

[http://www.gnutellaforums.com/showth...threadid=54814](http://www.gnutellaforums.com/showth...threadid=54814)

---

### Post by Edward The Bonobo on 2006-03-30
404 on that one.

---

### Post by LanceM on 2006-03-30
chopped it...maybe this will work.
```
http://www.gnutellaforums.com/showthread.php?threadid=54814
```

Sorry for the need to copy and paste, but at least it shows the right url.

---

