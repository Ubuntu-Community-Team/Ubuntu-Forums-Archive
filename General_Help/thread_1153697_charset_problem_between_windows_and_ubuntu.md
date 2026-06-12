---
title: "charset problem between windows and ubuntu"
date: 2009-05-09
forum: General Help
---

### Post by fredu on 2009-05-09
Hi folks,

I m a new user of Ubuntu and i find it great except for one little detail... 

Thanks to read my thread! ;)

I installed Ubuntu Gnome on a laptop with which i usually use windows xp. As recommended in a tutorial, i created 4 partitions:
- c: NTFS for windows
- / ext3 for ubuntu
- /home ext3 for a file syst. that would be shared by the two OS
- and a swap partition

I use a tool (ext2fs something...) to be able to read the ext3 partitions from windows...

When I tried to transfer my files (I m a web developper) from windows to linux, i had problems with specialchars. I m french so i use this kindof things: é à è etc...

- bébé.txt created on windows and put in the /home directory becomes b&#65533;b&#65533;.txt on ubuntu
- bébé.txt created on linux becomes b?b?.txt on windows (actually, the ? would be some very weird chars like squares and so)

Whatsmore, if the file contains these accented characters, a less file.php would give something like 

//initialiser les propri<E9>t<E9>s 

which should be

//initialiser les propriétés 

(that means "initiate properties", that s actually a PHP comment).

Whats really weird is that if i open the file with the normal text editor (by double clicking on th icon), everything looks just fine. On the other hand, if I used Eclipse PDT (a PHP IDE) it give:

 //initialiser les propri&#65533;t&#65533;s

well...

Since my windows is in french, i guess its encoded in ISO-8859-1 or ISO-8859-15. My ubuntu is in UTF-8, but for many of the french people i talked to, they had no problem with a similar installation.

Here s the result of a locale:

```

LANG=fr_FR.UTF-8
LC_CTYPE="fr_FR.UTF-8"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_ALL=
```I tried many other things but nothing actually worked.

I ve been googling for about two days and i ve posted hundreds of threads so i really hope somone here can help me.

Thanks a lot

cheers

---

### Post by bobince on 2009-05-09
> I use a tool (ext2fs something...) to be able to read the ext3 partitions from windows...Well that's the rub, what's the exact tool? It's up to this to decide what character set to use for filenames; from your problems it sounds like it is choosing a Latin-1-based character set (ISO-8859-1/cp1252), which you don't want.

I've been using fs-driver.org's one and that's been behaving fine with UTF-8.

> Whatsmore, if the file contains these accented charactersAh well, the actual contents of the file don't change when transferred; it's up to the application reading them to decide what to do. PHP files are byte-oriented and have no associated charset information (unlike, say, XML, which can signal its own charset), so a text editor has to guess.

So it's just a case of asking your text editor to load them with the right chracter set. This isn't a locale issue as there may be files with many different charsets on the same system. Generally the simplest approach is to try to keep everything as UTF-8 when originally created; this would depend on how your Windows text editor is set up but most can be configured to save UTF-8 by default.

Although: with PHP, if you included actual content with UTF-8-encoded non-ASCII characters, rather than just PHP comments, that would also be changing the encoding of your final web pages. Which is probably a good thing, but it's best to signal that using the Content-Type header()/meta-tag, and if you've got database backing you have to be using UTF-8 for that too.

---

### Post by fredu on 2009-05-09
> Well that's the rub, what's the exact tool? It's up to this to decide what character set to use for filenames; from your problems it sounds like it is choosing a Latin-1-based character set (ISO-8859-1/cp1252), which you don't want.

Well, the tool is named ext2ifs. But i dont think the problem comes from here, or not entirely. I have a french windows and its charset is set to ISO-8859-1 not UTF8. If the problem came from the tool, shouldnt i have fine filenames on linux of files created on windows (even before having installed Ubuntu)? I m not sure...

> Ah well, the actual contents of the file don't change when transferred; it's up to the application reading them to decide what to do. PHP files are byte-oriented and have no associated charset information (unlike, say, XML, which can signal its own charset), so a text editor has to guess.

Ok i got that. So considered my files were written using ISO-8859-1 on windows, it means my Shell is set to UTF8 (i ve got these <E9> things), so is my Eclipse IDE (i ve got these weird &#65533;) , but my "normal editor" is set to ISO-8859-1 since it prints special chars correctly. 

> this would depend on how your Windows text editor is set up but most can be configured to save UTF-8 by default.

It would be set up to ISO8859-1, according to my windows charset... 

Is an english windows set to UTF8? What if i install an english one?

Or would it be possible to change my windows to UTF8? so i could change all my files from ISO to utf8 once for all?

> it's best to signal that using the Content-Type header()/meta-tag

This is what i usually do. I have a html meta saying:

```
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-15" />
```

Thanks for explanations ^^

---

### Post by bobince on 2009-05-10
> **fredu said:**
> I have a french windows and its charset is set to ISO-8859-1 not UTF8. If the problem came from the tool, shouldnt i have fine filenames on linux of files created on windows (even before having installed Ubuntu)?

If you're talking about viewing your Windows partition from Linux, that should generally work fine for NTFS (which supports Unicode), but can be troublesome for FAT32 (which is byte-based). But that's a separate issue to whether you can write files to ext2 from Windows.

For accessing ext2/ext3 partitions from Windows you get two choices with fs-driver's ext2ifs: either you can use UTF-8 (which is the right thing for Ubuntu and many other distributions), or you can use the Windows code page (which is usually the wrong thing unless by luck both installations are using the same locale... although see below for why they're rarely *exactly* the same).

So generally you want to [enable UTF-8 in fs-driver](http://www.fs-driver.org/ScreenSetup3.html).

> It would be set up to ISO8859-1, according to my windows charset...

Actually it'd be set to Windows Western European, code page 1252. This is similar to ISO-8859-1, but not quite the same. In particular there are different characters across the range 128-159; you tend to notice the problem when smart quotes are involved. Most of the Windows default system code pages are not-quite-standard mappings in this way.

> Is an english windows set to UTF8? What if i install an english one?

No, unfortunately UTF-8 cannot be used as a system code page on a Windows box. US-English (and British-English) Windows installs, like French, default to cp1252 (Western European). You can change the system code page from: Control Panel->System->Regional and Language Options->Advanced->Language for non-Unicode programs, then reboot.

---

### Post by fredu on 2009-05-10
> If you're talking about viewing your Windows partition from Linux, that should generally work fine for NTFS (which supports Unicode), but can be troublesome for FAT32 (which is byte-based). But that's a separate issue to whether you can write files to ext2 from Windows.

I m talking about viewing my ext3 FileSystem partition from both linux and windows. 

I cant see my windows partition from linux, since linux doesnt read NTFS.

> 
For accessing ext2/ext3 partitions from Windows you get two choices with fs-driver's ext2ifs: either you can use UTF-8 (which is the right thing for Ubuntu and many other distributions), or you can use the Windows code page (which is usually the wrong thing unless by luck both installations are using the same locale... although see below for why they're rarely *exactly* the same).

So generally you want to [enable UTF-8 in fs-driver]("http://www.fs-driver.org/ScreenSetup3.html").

I think here s the problem. I dont use ext2ifs because with that tool windows kept asking me to format partitions X:, Y:, Z: (respectively the new Ubuntu, FileSystem, and swap partitions) when i tried to open the drives in the windows workstation. On other forums, i ve been told to installed **ext2fsd** which is a similar applic, but **doesnt ask me wether i want to enable utf8**.

My question now would be: Imagine that my ext2fsd actually uses the utf8 code page (which i m really not sure of), would it "translate" files in both ways?

I mean, would it "translate" files from cp 1252 to utf8 (from windows to linux) when i write on my ext3 FileSystem partition from windows? And would it "translate" from utf8 to cp1252 when I write on this partition again, but from linux, whose text editors are encoded in utf8?

... hum... is it clear?


> Windows Western European, code page 1252. This is similar to ISO-8859-1, but not quite the same. In particular there are different characters across the range 128-159

Right! As usual, m* cant be bothered sticking to standards nor staying coherent even with itself (have you seen the dos code page? sth else again!)

Does someone know this ext3fsd program? and wether its possible or not to set the UTF8 option explicitly?

Thanks again

---

### Post by fredu on 2009-05-10
I m talking to myself...

So i found the solution to my problem, thanks to you guys cause you pointed the right things to check.

I appear to use Extfsd and not Extifs as a tool for beeing able to see (and write on) my ext3 partitions from windows.

Ext3ifs enable the utf8 option during the installation and so, you dont have to check that windows "knows" the partition s codepage is utf8. For pretty unclear reason, ext3ifs would ask me to format the ext3 drivers before beeing able to explore them. So i used ext3fsd instead.

Ext3fsd does not enable the utf8 default config. You actually have to open the program window, right click on the drive you want to setup, and select "Service Management" to set the codepage option on utf8. Rather sibyllin...

So i did that and after restarting, everything is just fine. I hope this topic will help other people with such problems.

Thanks so much for your help!

---

### Post by bobince on 2009-05-11
> For pretty unclear reason, ext3ifs would ask me to format the ext3 drivers before beeing able to explore them.

Curious, I've not seen that. You generally do have to tell it to pick up the drives manually by using the Ext2IFS entry in Control Panel, if you hadn't yet done that; otherwise dunno!

I've not tried ext2fsd, but glad you got it working!

> I cant see my windows partition from linux, since linux doesnt read NTFS.

Ubuntu doesn't mount Windows partitions automatically, but it can certainly access them, using the great ntfs-3g tool. eg. “sudo mount -t ntfs-3g /dev/sda1 /somemountfolder”.

> would it "translate" files from cp 1252 to utf8 (from windows to linux) when i write on my ext3 FileSystem partition from windows?

If you mean the content of files, no, that will never be touched. At a filesystem level there is no way to know whether a file contains cp1252 or UTF-8, or a load of binary gunk that is neither.

> linux, whose text editors are encoded in utf8?

Not really, that's entirely an application-level issue. Most Linux and Windows text editors (even Notepad) can load and save in any encoding. It is quite normal to have a mixture of files whose contents are cp1252, UTF-8, and even other encodings on both Windows and Linux.

For sanity, Linux and most of the rest of the world is moving towards using UTF-8 for everything always. It's a good place to aim for, but there is still a lot of legacy non-UTF-8 content out there.

---

### Post by fredu on 2009-05-11
> You generally do have to tell it to pick up the drives manually by using the Ext2IFS entry in Control Panel, if you hadn't yet done that; otherwise dunno!

Yes, this is what I did.


> Ubuntu doesn't mount Windows partitions automatically, but it can certainly access them, using the great ntfs-3g tool. eg. “sudo mount -t ntfs-3g /dev/sda1 /somemountfolder”.

Ok I didnt know. Would you recomand i install the application to see my windows partition from windows?
> 
If you mean the content of files, no, that will never be touched.

My english doesnt make it easy ;) This is what I ment...

---

