---
title: "Websites that &quot;REQUIRE&quot; Microsoft Internet Explorer - HELP!"
date: 2006-07-10
forum: Desktop Environments
---

### Post by em3raldxiii on 2006-07-10
Okay, I've searched the forum ... but I think the "new" forum format is making it more difficult to find what I need.  So I appologize if this is a repeat thread (I am willing to bet someone has asked this question before) ...

So, my dad uses [http://abmls.mlxchange.com](http://abmls.mlxchange.com) for business (he's a real estate agent), but he's recently had a number of severe security breaches in his M$ Win2kPro.  In fact, the security issues are so bad that he is now willing to try Linux (bloody virus that keeps sneaking back in and I can't seem to eradicate it for longer than a few days ... pesky thing).  It's important to note that he's 56 years old, and not exactly a computer whiz ... but he's seen how my Ubuntu system has been running for over 3 months without a full reboot.

But when I tentatively tried his business website (which he absolutely requires to do his job), the site refuses to allow access to any browser other than IE.

SO.  Is there a magical Linux browser that will dupe that site?

I have tried:  Konqueror, Firefox, and Opera.  I even tried setting Firefox and Opera into "reporting" itself as MSIE.  No luck.

HELP!

---

### Post by raldz on 2006-07-10
Install IE6 using wine..

install wine first from the repos, then run "winecfg" to configure settings.. then right click on your IE installer and choose run with wine..

if you have little trouble, this short how-to may help:

[http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)

---

### Post by kickaha on 2006-07-10
I would also politely ask the hosting site to not code to IE-specific tags.

If everyone who said, "Huh? Why can't I see that?" would politely send a message to the host, and say they are not running IE, a shift of page coding practice could follow.

---

### Post by angkor on 2006-07-10
You could also look into setting up windows in a VMware Server (provided your father as a fast computer). That's what I do to circumvent these kind of problems. I also send an email to the webmaster btw.

---

### Post by em3raldxiii on 2006-07-10
Well, thanks for the extremely quick feedback!  I have to say, yet again, that these forums are a phenomenon unto themselves.  I have never seen a web forum as complete, friendly, and easy to use in my entire life.  This board alone is a spectacular feature that makes Ubuntu better than Windows ... and other distros actually.

Anyway, back to the problem at hand.  I was actually aware of VMware prior to posting my question, but had resisted the idea of using it.  I mean, why do it if there is a native client program to do it?  In a way, installing Windows via VMware is almost like admitting that one can't live without Microsoft.  I am sure someone will some day code a browser (or plugin) specifically for circumventing this sort of thing.

As far as WINE goes, well, I had a bittersweet experience with it about 2 years ago when I experimented with Mandrake 9, and I have sorta shied away from it since.  On the other hand, i think I will try it first because it's a little closer to "avoiding a reliance on microsoft".

My aversion to Microsoft is mostly principle, really.  It's not that I truly hate the company or anything (though I understand why some people might).  It's more that I like to commit to a plan and a path and I don't want to "give up" and fall back to their software.  It's almost a statement of pride, "I am microsoft free," "All my software is free, legally."

I'll let you all know if Wine/IE is easy ... and doable by a user like my dad. :D :KS

---

### Post by aysiu on 2006-07-10
Google IEs4Linux.

---

### Post by HAARP on 2006-07-10
Try deactivating Javascript in Firefox
Download the User Agent Switcher extension and set it to IE
That should do the job

edit: oops, actually, that site doesn't work without Javascript :s

---

### Post by celticmonkey on 2006-07-10
I think you've already tried these, but just to re-iterate:

1) install Opera. It fools websites into thinking you are using IE.

or

2) install an extension for Firefox called User Agent Switcher that does the same thing:
[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)


That should solve the problem for any site -- unless it needs Microsoft's Active X. There is an Active X plugin out there for Firefox, although I have no idea if it would work with linux.

---

### Post by aysiu on 2006-07-10
> **celticmonkey said:**
> I think you've already tried these, but just to re-iterate:

1) install Opera. It fools websites into thinking you are using IE.

or

2) install an extension for Firefox called User Agent Switcher that does the same thing:
[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)


That should solve the problem for any site -- unless it needs Microsoft's Active X. There is an Active X plugin out there for Firefox, although I have no idea if it would work with linux.
You might have missed this last part of the original post: > I have tried: Konqueror, Firefox, and Opera. I even tried setting Firefox and Opera into "reporting" itself as MSIE. No luck.

HELP! In my experience, User Agent Switcher handles just about anything. There are, however, a small handful of sites that it can't handle, and these do not necessarily use ActiveX.

For those sites, IEs4Linux is the way to go.

---

### Post by hayesey on 2006-07-10
I know this isn't helping your immediate problem but I'd seriously get your dad to complain to his web development company about that.  A sizable (and increasing) percentage of people are now using Firefox instead of IE in Windows.  If he isn't already losing business because of it I'm sure he will start to do so soon.

---

### Post by Orval on 2006-07-10
You didn't try Konqeuror reporting itself as IE? I have had luck with Konqueror with some websites.

---

### Post by DirtDawg on 2006-07-10
> **aysiu said:**
> There are, however, a small handful of sites that it can't handle, and these do not necessarily use ActiveX.

For those sites, IEs4Linux is the way to go.

I think Aysiu is right on the money on this one. [The home page]("http://www.tatanka.com.br/ies4linux/index-en.html") even sez:
  
"""
What is the target public?
    * WebDesigners that want to move to Linux but still need to test their sites on IE.
    *** People who have to open IE-only sites**
"""

You do not like IE you say? Try it try it and you may. Try it and you may I say.

---

### Post by em3raldxiii on 2006-07-10
Well, I haven't tried every route yet ... I'll go over the firefox plugin thing again to see if I missed something.

IES4Linux looks fantastic, but I had some troubles during the install:

>  Extracting CAB files
/home/em3rald/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 1372578 extra bytes at end of file.
ie_3.cab: checksum error
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 1372578 extra bytes at end of file.
ie_4.cab: checksum error
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 948554 extra bytes at end of file.
ie_5.cab: checksum error
/home/em3rald/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/em3rald/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 766570 extra bytes at end of file.
vbscript.dll: checksum error
/home/em3rald/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 692558 extra bytes at end of file.
comctl32.dll: checksum error
/home/em3rald/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 1012088 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.


(I posted this elsewhere on this forum too).

Anyhoo ... apparently this problem has occurred for others too.  I have tried redownloading the files in case they were corrupted during transfer, but with no luck.  Each time I did so, the # of extra bytes was different.

I'll keep you all posted on that front.

And as far as the website development is concerned, well ... my dad is just a client to the mlxchange site which is huge.  I am somewhat dubious about them choosing to change any time soon, but I will indeed recommend to him that he try to contact them and "politely" complain.  I am a steadfast Opera user, personally, but I don't mind using Firefox.

Later!

---

### Post by em3raldxiii on 2006-07-10
quick note ... I just made sure I had the firefox plugin.  The page just shows up blank now in firefox.  No errors, but no content either.

---

### Post by em3raldxiii on 2006-07-10
New quick note ... tried IEs4Linux a few more times ... now the "extra bytes" are the same each time, even after deleting the files and re-downloading everything.  Identical errors every time.

---

### Post by Case_f on 2006-07-10
Opera 9 has new options regarding this issue - it has the option 'Identify as IE', in which case it identifies as IE, but still renders the page as Opera would, and then it also has the 'Mask as IE' option, which not only identifies Opera as IE, but also renders pages more like IE would. It's now available in Dapper repositories, if I'm not mistaken.

EDIT: Ooops, sorry, my mistake, doesn't help in this case. I apologize...

---

### Post by em3raldxiii on 2006-07-10
Okay, new NEW quick update.  I decided to be tenacious and completely remove ies4linux and then reinstall. and it worked!  Now just to get activeX to work ....

---

### Post by em3raldxiii on 2006-07-10
Hmm, well I went to [This Site]("http://www.pcpitstop.com/testax.asp"), and it tells me that "ActiveX is not supported" by my browser. (ies4linux).  Others have said that activex works fine on their installations, so I am at a bit of a loss here.  Anyone have experience with ActiveX and ies4linux?

---

### Post by mikeoh on 2006-07-11
If you realy need Internet Explorer I would recommend Crossover Office.  Its not free but its well worth the price and for me it has flawlessly installed Internet Explorer more then once.

---

### Post by galv on 2006-07-11
> **mikeoh said:**
> If you realy need Internet Explorer I would recommend Crossover Office.  Its not free but its well worth the price and for me it has flawlessly installed Internet Explorer more then once.
I agree, Crossover Office is the way to go if you really need a Windows app, like IE.
And the price you pay is cheaper than Windows licence (and anti-virus licence, and ...)
You can give it a try, in their website there is a demo you can test for 30 days.

Galv

---

