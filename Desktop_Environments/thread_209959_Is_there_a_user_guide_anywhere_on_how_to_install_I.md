---
title: "Is there a user guide anywhere on how to install Internet Explorer on Ubuntu?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by RAV TUX on 2006-07-05
I would like to get Internet Explorer running on Ubuntu. I have Wine but I am not sure how to do this. Can anyone help me here or direct me to a users guide on how to do this?













.

---

### Post by evilghost on 2006-07-05
First question:  Why on Earth would you do this, especially since we are on the cusp of two critical updates for IE on the next unholy incarnation of 'Typical Tuesday'.

Answer:  Consider using WineTools for the IE6 installation, however, beware as some version of WINE fail to correct install IE reporting various errors such as "Installation package corrupt" to "Failed to download".

---

### Post by srunni on 2006-07-05
There are many good reasons to install IE in Ubuntu. One major need is for web developers to be able to be able to easily check if their websites render correctly in IE.

---

### Post by msak007 on 2006-07-06
There are numerous posts on this already, but there are several ways to get IE in Ubuntu. evilghost already mentioned [WineTools]("http://www.von-thadden.de/Joachim/WineTools/") (which is the method that I use - useful for more than just IE), but as mentioned you have to be careful with that because some versions of wine have a bug that doesn't let you install IE and it errors out. I've only had success by adding the [Wine HQ repositories]("http://www.winehq.com/site/download-deb") and installing wine from there rather than from the official Ubuntu repos. The other way I know of and have used is [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html"). That method installs IE (multiple versions, if you need them) and runs it great, but won't help if you want to install apps using wine that require IE because the script installs IE in a different directory. Your best bet is to use WineTools in that scenario.

---

### Post by musicinmybrain on 2006-07-06
[QUOTE=srunni]There are many good reasons to install IE in Ubuntu. One major need is for web developers to be able to be able to easily check if their websites render correctly in IE.[/QUOTE]

Very true. I might mention, though, that for those who don't need IE very often and can deal with a short wait, [http://browsershots.org](http://browsershots.org) can be a good solution.

---

### Post by em3raldxiii on 2006-07-10
I attempted to install IEs4Linux, but it apparently has some kind of problem - although this might actually be MSIE's fault.  When it tries to extract some of the CAB files, I get a large output like this:

> 
 Extracting CAB files
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


According to *their* forums, this is a relatively common problem, and the jury is still out as to what is causing it.  I have tried re-downloading the files a few times (they're the M$ files), but to no avail.  It should be noted that the # of "extra bytes" changes slightly each time I download it.  Any thoughts?

---

### Post by RAV TUX on 2006-07-13
> **msak007 said:**
>  The other way I know of and have used is [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html"). That method installs IE (multiple versions, if you need them) and runs it great, but won't help if you want to install apps using wine that require IE because the script installs IE in a different directory. Your best bet is to use WineTools in that scenario.

I installed IE with Wine, thanks to the help here and mostly thanks to the new "Ubuntu Hacks" book I bought lastnight but here is the problem I couldn't get launchcast to play, it just stays on tuning but doesn't play.

This is important, my wife wants to be able to play launchcast on Ubuntu.

I think it may have something to do with script installs?

anyway here is the question for IE 6 do I need to buy a CD?

or can I burn a copy from my XPsp2 system?

just trying to get this to run.

any help is much appreciated.

---

### Post by Billquinn1 on 2006-07-13
> I couldn't get launchcast to play, it just stays on tuning but doesn't play.

Did you also install windows media player? Somehow it needs that to play.
It is an option when you run winetools. 

> anyway here is the question for IE 6 do I need to buy a CD?
or can I burn a copy from my XPsp2 system?

Microsoft would probably like for you to own a copy but I'm thinking you can't make them happy any way so I think the copy you own on your XP system will be good enough. I am not sure what you mean about burning a copy though?

---

### Post by RAV TUX on 2006-07-13
> **Billquinn1 said:**
> Did you also install windows media player? Somehow it needs that to play.
It is an option when you run winetools. 



Microsoft would probably like for you to own a copy but I'm thinking you can't make them happy any way so I think the copy you own on your XP system will be good enough. I am not sure what you mean about burning a copy though?

Winetools I didn't actually load the winetools I must need to do that yet.

burning a copy? I'm not sure what I mean either.

---

### Post by Billquinn1 on 2006-07-13
This guide is excellent for getting your wine setup with IE and media player. After you get it all good just don't upgrade to a newer wine or it will break your IE.


> [http://doc.gwos.org/index.php/WineSetup](http://doc.gwos.org/index.php/WineSetup)

You may have already done a lot of this so look it over to see what you think.

---

### Post by RAV TUX on 2006-07-14
> **Billquinn1 said:**
> This guide is excellent for getting your wine setup with IE and media player. After you get it all good just don't upgrade to a newer wine or it will break your IE.




You may have already done a lot of this so look it over to see what you think.

Thanks, going to look over it now. 

I have yet to figure out how to get winetools running? I tried the tar gz file but no luck...

ok let me check out your link, thanks.

---

