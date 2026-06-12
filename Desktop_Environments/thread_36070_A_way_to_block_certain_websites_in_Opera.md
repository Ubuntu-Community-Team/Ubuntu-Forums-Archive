---
title: "A way to block certain websites in Opera?"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Jaivaz on 2005-05-21
Is there a way to block certain websites in Opera?

---

### Post by Xian on 2005-05-21
It uses the host file so you can block websites there.
Here's the procedure:

1. Empty the Disk Cache in Opera 8
Tools > Preferences > Advanced > History > 'Empty Now'

2. Close Opera

3. In a terminal enter this command:
```
sudo gedit /etc/hosts
```

4. Append at bottom of that file what website(s) you would like to block. 
Use the format provided with the prefacing 127.0.0.1 and then the site.
Here's an example where I'm blocking [www.cnn.com:](www.cnn.com:)

```
#Website Block
127.0.0.1  www.cnn.com
```

5. Open Opera

6. Goto blocked website and see it not load. :)

---

### Post by Jaivaz on 2005-05-21
Thank you Xian, it worked perfectly.

---

### Post by bored2k on 2005-05-21
I'm guessing it also works with FF. Thanks for the tip. Now I can block those annoying pr0n sites before they appear :D No more massive adblock images!

---

### Post by GTvulse on 2005-05-21
[QUOTE=bored2k]I'm guessing it also works with FF. Thanks for the tip. Now I can block those annoying pr0n sites before they appear :D No more massive adblock images![/QUOTE]
 For FF  it is better to use adblock ([http://adblock.mozdev.org/](http://adblock.mozdev.org/)) with the filters available at [http://www.geocities.com/pierceive/adblock](http://www.geocities.com/pierceive/adblock). There are other advert blocking extensions for FF but IMHO adblock does its job extremely well.

---

### Post by lotusleaf on 2005-05-22
To add to Xian's nice post regarding the hosts file, I copy/paste the [mvps hosts file](http://www.mvps.org/winhelp2002/hosts.htm) into my /etc/hosts file (removing the duplicate localhost entry which is added when copy pasting this into your hosts file). It's huge, updated often, and blocks just about any advertisement I've come across on the web so far. I don't bother with browser plugins/extensions/whatever. They may work fine, but I've always found that using an effective hosts file works best.

---

### Post by tread on 2005-05-22
Thanks for the hosts file .. I never thought of using the hosts file to block ads .. duh! :)

---

### Post by NuLLCoDe on 2005-06-02
It uses the host file so you can block websites there.
Here's the procedure:

1. Empty the Disk Cache in Opera 8
Tools > Preferences > Advanced > History > 'Empty Now'

2. Close Opera

3. In a terminal enter this command:

Code:

sudo gedit /etc/hosts


4. Append at bottom of that file what website(s) you would like to block. 
Use the format provided with the prefacing 127.0.0.1 and then the site.
Here's an example where I'm blocking [www.cnn.com:](www.cnn.com:)


Code:

#Website Block
127.0.0.1  [www.cnn.com](www.cnn.com)


5. Open Opera

6. Goto blocked website and see it not load. 
__________________
If all you have is a hammer you tend to see every problem as a nail.









Where is a terminal window??? :confused:

---

### Post by bluesman2333 on 2005-06-10
Where is a terminal window??? :confused:

What you want to do is start a terminal session. It should be in your Gnone menu somewhere. 

For Kubuntu users, an easy way is to kmenu-system-terminal program(Konsole) then type "sudo kate", enter pwd, then copy paste the contents of the .txt file off of  the mvps web site into the etc/hosts file on your machine.

---

### Post by Xian on 2005-06-10
[QUOTE=bluesman2333]What you want to do is start a terminal session. It should be in your Gnone menu somewhere.[/QUOTE]
Just right-click on your desktop and choose "Open Terminal".

Here's an easy way to add entries to your hosts file. 
Let's suppose we want to add this addy: ad.adclick2.com

Open a terminal and enter this command:

```
$ sudo echo "127.0.0.1  ad.addclick2.com" >> /etc/hosts
```

---

### Post by dakira on 2005-07-04
Regarding Opera and blocking stuff you might be looking for filter.ini. The file is located in the .opera directory in your home directory.

If you want to use it for ad-blocking in Opera I would recommend CSS-based blocking over URL/IP-based blocking.. See the [Opera Wiki](http://nontroppo.org/wiki/Opera) for details (link below).

[http://nontroppo.org/wiki/BlockAdvertisements](http://nontroppo.org/wiki/BlockAdvertisements) 

If you have questions on CSS-based AdBlocking feel free to ask me!

Cheers
dakira

---

### Post by r0nin on 2005-10-18
[QUOTE=lotusleaf]To add to Xian's nice post regarding the hosts file, I copy/paste the [mvps hosts file](http://www.mvps.org/winhelp2002/hosts.htm) into my /etc/hosts file (removing the duplicate localhost entry which is added when copy pasting this into your hosts file). It's huge, updated often, and blocks just about any advertisement I've come across on the web so far. I don't bother with browser plugins/extensions/whatever. They may work fine, but I've always found that using an effective hosts file works best.[/QUOTE]

I know the hosts file trick from Windows and always used it then. Now with Linux & Opera/ FF tough it doesn't work. When Opera tries to load a blocked add it just keeps trying to connect to the the addserver and doesn't render the site for me to use.

---

### Post by dakira on 2005-10-19
Hi,

I wrote a very small shell script to activate CSS-based AdBlocking in Opera. I prefer CSS based blocking since it actually removes the elements. with filter.ini you still have the ugly spaces (since the space for the images is still reserved).

Hope you like it.

---

