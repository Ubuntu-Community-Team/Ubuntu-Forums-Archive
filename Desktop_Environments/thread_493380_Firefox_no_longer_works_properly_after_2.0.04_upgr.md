---
title: "Firefox no longer works properly after 2.0.04 upgrade"
date: 2007-07-05
forum: Desktop Environments
---

### Post by MystaMax on 2007-07-05
After allowing firefox 2.0.0.4 to upgrade (via firefox upgrade, not synaptic), I  have to launch firefox 3 times on some occasions for it to launch. Each time I launch firefox, it'll say "Starting Firefox" in my lower panel, but never starts. A lot of my extensions no longer work, such as:

keyconfig
firebug
delicious (very annoying)
google notebook
colorzilla
greasemonkey

I've been dealing with this since 2.0.0.4 was released. Its really starting to impede on my workflow. Can anyone recommend what I should do?

I don't mind starting off fresh with a fresh copy of firefox. Whats the best way to just start fresh? Can synaptic handle this? Are there any directories that need to be manually deleted, so that none of these 'problems' are 'cached' for lack of a better word. 

The only thing I'm truly concerned about is my passwords, and I know I can backup the key3.db file in my mozilla profile.

Any help is appreciated. Thanks! :)

---

### Post by scxtt on 2007-07-05
what happens (what's it print out) if you launch firefox from the terminal?

---

### Post by MystaMax on 2007-07-05
Hi scxtt, thanks for the reply.

The first time I ran "firefox" from the terminal, I received the following:

> 

Segmentation fault (core dumped)

It showed "starting firefox" in lower panel, and then disappeared. I tried it again and the usual appeared:

> 

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed



---

### Post by scxtt on 2007-07-05
what's in **~/.fonts.conf**? [ *cat ~/.fonts.conf* ]

---

### Post by MystaMax on 2007-07-06
Here it is below:

[http://paste.ubuntu-nl.org/28804/](http://paste.ubuntu-nl.org/28804/)

I'm not sure what its suppose to look like, but I think I remember this popping up when I had Dapper installed. This is a fresh install of Feisty (installed @ release). 

Thanks :)

---

### Post by scxtt on 2007-07-06
the main difference i see b/t yours and mine is:

_YOURS_:
<?xml version=&#8221;1.0&#8221; ?>
<!DOCTYPE fontconfig SYSTEM &#8220;fonts.dtd&#8221;>

_MINE_:
<?xml version=&#8221;1.0&#8221;?><!DOCTYPE fontconfig SYSTEM &#8220;fonts.dtd&#8221;>

so, 1st thing i'd try is to bring what's on line 2 up to what's on line 1 ...

---

### Post by MystaMax on 2007-07-06
hmm, I'm not sure whats up...

I made the changes adding line 2 to line 1, but the results were the same. I then searched google for ".fonts.conf" and it came back with [this result]("http://fontconfig.org/fontconfig-user.html"). This site states that the formatting in my file is correct.
[B]
**EDIT**[/B]
Now that I think about it, maybe the spacing from the left on lines 2 and so forth need to be indented like the example below?

> 

Configuration files for fontconfig are stored in XML format; this format makes external configuration tools easier to write and ensures that they will generate syntactically correct configuration files.  As XML files are plain text, they can also be manipulated by the expert user using a text editor.   
The fontconfig document type definition resides in the external entity "fonts.dtd"; this is normally stored in the default font configuration directory (/etc/fonts).  Each configuration file should contain the following structure:     
    ```
<?xml version="1.0"?>
    <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
    <fontconfig>
    ...
    </fontconfig>
```    I don't think this is causing problems w/ my extensions and overall Firefox functionality. But , now I'm concerned, & I'd like to fix it anyway. I remember seeing this error when I launched Firefox via CLI in dapper.

I'm nervous about uninstalling Firefox b/c I know it has alot of dependencies that I know I shouldn't uninstall. I'm surprise no one else has had the same problems as me.

I'm going to try disabling each extension one by one and see if its a particular one that is causing the problem. Hopefully it'll provide some feedback.

Any other tips or information to help resolve my problem here?

---

### Post by Hickler on 2007-07-06
Hello, I'm new to Ubuntu/Linux however I'm having the same problem as you.. I hope you manage to fix it and can get back with a solution. Thanks.

---

### Post by scxtt on 2007-07-06
mine looks just like this:
```
:> cat .fonts.conf
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

---

### Post by avik on 2007-07-06
This is the XML declaration that MystaMax has:

```
<?xml version=&#8221;1.0&#8221; ?>
```

Get rid of the space between the " and the ?, like so:

```
<?xml version=&#8221;1.0&#8221;?>
```

---

### Post by MystaMax on 2007-07-07
Hi avik-

I tried this already as its one of the things I noticed. But, I got the same results.

Hickler, which one of my problems are you having? the fons.conf problem? Or FireFox not loading properly and extensions not working at all. I can't even check the options of extensions I listed above.

---

### Post by szf on 2007-07-07
> **MystaMax said:**
> After allowing firefox 2.0.0.4 to upgrade (via firefox upgrade, not synaptic), I  have to launch firefox 3 times on some occasions for it to launch. Each time I launch firefox, it'll say "Starting Firefox" in my lower panel, but never starts.
I share these extensions with you:
  firebug 
  delicious
  google notebook
  colorzilla
And had the exact same problem. I was able to start firefox from Gnome Terminal with the ProfileManager option.
```

[FONT="Courier New"]**$ firefox -ProfileManager &**[/FONT]

``` 
I created a new Profile and it's all better. I don't recall deleting the default profile, but now it just works.

You may want to be sure to back up you password keystore to a known location if you do this.

---

### Post by MystaMax on 2007-07-09
Hi szf,

Thanks for providing that input. I tried your suggestions and I got about 70% of what I was looking for. Delicious, Google Notebook, and firebug still would not work properly. I decided to install Firefox from Mozilla as oppose to using the Ubuntu build. I used the [ubuntuzilla]("http://ubuntuforums.org/showthread.php?t=421370") scripts to get it working properly. Its pretty automatic and painless.

I was also reading [this thread]("http://ubuntuforums.org/showthread.php?t=494942") about another user having troubles. That thread collected many users opinion about performance and other problems they see with Firefox on Ubuntu. 

I'm just glad I got it working... at least for now ;)

---

### Post by djhworld on 2007-07-12
Hi there,

I was having the same trouble as you and I found the root cause of the problem (I hope)

Uninstall colorzilla.

That's the extension that seems to screw things up for me (firefox works perfectly fine after the uninstallation!)

---

### Post by MystaMax on 2007-07-12
wow, so all your extensions just started working right after uninstalling Colorzilla? I wonder if this is specific the Ubuntu version of Firefox and Colorzilla. 

The Colorzilla website recommends installing the Mozilla build.

---

### Post by VictorR on 2007-07-12
I did not have problem like yours with Firefox, but I noticed that after upgrading to 2.0.0.4 I got memory leak. I searched for the solution in the Internet and I found that there are some other Mozilla based browsers. I installed Swiftfox just to try and was impressed as it had adopted all my bookmarks and settings from Firefox (i did nothing for this, it had found and taken them itself).
So I am pretty happy now - Swiftfox looks and behaves exactly like Firefox does, runs faster, and no more memory leaks.
[http://getswiftfox.com/](http://getswiftfox.com/)
I can't guarantee anything but for me it was the simplest solution.

---

### Post by handy on 2007-07-13
I just upgraded Firefox on my Dapper machine, it worked smooth as glass, used all my previous settings, bookmarks & no memory leak.

By comparison, after following a Ubuntu firefox upgrade how-to & trashing the OS on my Breazy box 18 months or so ago, I found this update to be the way they should be.

Unfortunate that others are having trouble.

---

### Post by scxtt on 2007-07-13
it's no miracle that swiftfox or a new version of firefox has the same bookmarks/settings - all that stuff is stored in your home directory, probably in ~/.mozilla ...

---

### Post by bonzodog on 2007-07-13
One of the things you could do is delete the profile directory in ~/.mozilla., but it does sound like the problem is connected to the Ubuntu build of 2.0.0.4 using the colorzilla extension.

---

### Post by eoshicute on 2007-07-13
firebug is can't work at firefox 2.0.0.4, because a diferent code from the older version of firefox

you must wait a newer version of firebug :)

---

### Post by handy on 2007-07-14
> **scxtt said:**
> it's no miracle that swiftfox or a new version of firefox has the same bookmarks/settings - all that stuff is stored in your home directory, probably in ~/.mozilla ...

Yes, I know...

All don't though, so hopefully you may help someone.

---

### Post by hugobarauna on 2007-07-21
> **djhworld said:**
> Hi there,

I was having the same trouble as you and I found the root cause of the problem (I hope)

Uninstall colorzilla.

That's the extension that seems to screw things up for me (firefox works perfectly fine after the uninstallation!)

I uninstalled and my fireox is now working rigth. Thanks!

---

### Post by crimesaucer on 2007-07-21
> **MystaMax said:**
> Hi scxtt, thanks for the reply.

The first time I ran "firefox" from the terminal, I received the following:

```
Segmentation fault (core dumped)
```

It showed "starting firefox" in lower panel, and then disappeared. I tried it again and the usual appeared:

```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```

Hello, I'm not an expert but it looks like you have two different problems. I don't know about the "Segmentation fault (core dumped)" problem...


...but I know why you have the other "usual" error of "Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed".


The reason why is that the code from the wiki page for smooth fonts has the wrong "quote marks" in the code, so the smooth fonts don't even work because of the "Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed".


I had the same error, and when I fixed it to look like this in my .fonts.conf, it looked a lot better

Just paste this into your .fonts.conf

```

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

```


This won't fix Firefox, but it will stop that error every time you use the Terminal...and it will make you fonts really nice like this: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-50-6.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-50-6.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-50-7.png[/IMG]

---

### Post by crimesaucer on 2007-07-21
> **MystaMax said:**
> Here it is below:

[http://paste.ubuntu-nl.org/28804/](http://paste.ubuntu-nl.org/28804/)

I'm not sure what its suppose to look like, but I think I remember this popping up when I had Dapper installed. This is a fresh install of Feisty (installed @ release). 

Thanks :)

The quote marks are "italicized" in the code of that page and in the ubuntu wiki pages...

The code is correct, so just write it with new "regular" quote marks and you will get really smooth fonts in your apps like mousepad or whatever notepad you use.

Here is the code with the corrected quotes:

```

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

---

