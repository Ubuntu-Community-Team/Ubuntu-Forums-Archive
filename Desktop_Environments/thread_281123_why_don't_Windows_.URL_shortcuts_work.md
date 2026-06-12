---
title: "why don't Windows .URL shortcuts work?"
date: 2006-10-20
forum: Desktop Environments
---

### Post by bsmith1051 on 2006-10-20
In Windows you can create a .URL shortcut file by simply dragging-and-dropping the Address from IE (or Firefox) to the desktop; yes, I know you can do this part, too, in Ubuntu.  The resulting Windows .URL file is simply a text file containing the URL, e.g. http://www.ubuntu.org

When you try to use this file in Ubuntu, however, you get various error messages.  Isn't this a really simple issue?  If you double-click on the .URL file (and also if you rename it .TXT first) Ubuntu recognizes it as file-type "x-mswinurl" and then refuses to open it.  You can't even view it, i.e., to manually copy-and-paste the URL into Firefox.

Is this a bug in the recognition code of the "x-mswinurl" file-type definition?

---

### Post by DC@DR on 2006-10-20
Didn't get your point...the URL address you dragged and dropped to the desktop will be automatically saved in .txt format, which includes the url address, never seen smth like "x-mswinurl" as you mentioned...

---

### Post by bsmith1051 on 2006-10-20
the file was originally created on a Windows system and is now called, e.g. "shortcut.url".  Trying to use that same file under Ubuntu just results in error messages even though it's a simple text file.  If you look at the properties assigned to it under Ubuntu, it's marked as file-type "x-mswinurl".

---

### Post by DC@DR on 2006-10-20
OK, now I got your point, you mean that shortcut is created originally on a Windows system, not from Ubuntu...I never did that, so that's why I didn't recognize the file-type "x-mswinurl". I guess Ubuntu can't read it since Windows-specific file-type is not in as open standards as in Linux, well, it's Windows anyway, don't expect to open anything from Windows world right away in Linux world, for example .wmv or .avi file-type, unless you do some hacks :)...

---

### Post by bsmith1051 on 2006-10-20
> **DC@DR said:**
> I guess Ubuntu can't read it since Windows-specific file-type is not in as open standards as in Linux
It's just a plain ASCII text file!  The fact that the file extension is ".url" is the only key to it's contents and hardly constitutes proprietary and inaccessible IP.  Here's an actual example:

```
[DEFAULT]
BASEURL=http://www.yahoo.com/
[InternetShortcut]
URL=http://www.yahoo.com
Modified=50834676ADF4C601F7
```

---

### Post by airtonix on 2006-10-22
well you do realise this isnt a bug to do with linux or ubuntu, but rather the linux version of firefox.....

Try repeeating you attempts with konqueror (i know a kde thing)....or another gnome type browser.

---

### Post by bsmith1051 on 2006-10-23
> **airtonix said:**
> this isnt a bug to do with linux or ubuntu, but rather the linux version of firefox.....
Are you sure?  I can't even view the file in gedit (which is part of Ubuntu and/or Gnome, right?)  It says, "gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file."  If I choose Character Coding = "Current Locale (UTF-8)" or "Western (ISO-8859-15)" it still fails.

UPDATE:  
Strange, I'm able to open _some_ .URL files but not others.  The ones which are at least viewable then give this Gnome error message when you try to open them normally:
> "The filename 'example.url' indicates that this file is of type 'resource location'.  The contents indicate that the file is of type 'application/x-mswinurl'. Rename the file to the correct extension for 'application/x-mswinurl' and then open the file normally.  Alternatively, use Open With to choose an app."
If you try the latter and choose Firefox, it gets caught in a loop where it keeps prompting you whether to Open or Save the 'resource location' and then opening additional blank windows with the same prompt.

So it seems like there are 2 bugs here:
1. Gnome doesn't correctly identify the plain-ASCII contents of most Windows-created .URL files
2. Gnome and/or Firefox treat Windows-created .URL files as Linux-type 'resource location' files even though the contents are (I'm assuming) formatted differently.

---

### Post by tturrisi on 2006-10-23
afaik, .URL extension is a Windows-Mac only file format. Actually, the extension is cross platform but the file type url-internet shortcut is what I am referring to. There are linux apps that can be installed to handle these shortcut files.  The MSIE Internet Shortcut is a proprietary file type.

I emailed myself a Windows .url to Google & also made one on linux using Firefox.  Both are on my linux desktop.

Windows Internet Shortcut
```
[DEFAULT]

BASEURL=http://www.google.com/

[InternetShortcut]

URL=http://www.google.com/

Modified=30054C3C05F7C60180
 
Properties:
name: Google.url
mime-type: text/x-uri

```

Firefox link to Google
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=link to Google
Type=Link
URL=http://www.google.com/
Icon=gnome-fs-bookmark

Properties:
type: desktop configuration file
mime-type: application/x-desktop
```

Now, to answer the thread title question:
why don't Windows .URL shortcuts work?
The same reasons that you can't just run a .DLL or other windows file types like .EXE.

---

### Post by james_san on 2006-10-23
Well that's quite a silly answer really. .dll and .exe files are native binary files that require the win32 api. .url files are a simple text file.

There is no reason why this type of link couldn't be handled under linux, it is a very basic file format. One way to do it would be for firefox to handle a link like this, by recognising it and opening the url. Then gnome could associate .url files with firefox.

Another way would be for gnome (specifically nautilus - the file browser) to understand the .url file as a link, and open it in the default web browser (probably better, but could be messy since as far as I know it would be the only other link-file-type apart from .desktop)

Perhaps you could ask this question to the gnome developers? Like I said, it wouldn't be very hard to do...

---

### Post by ice60 on 2006-10-24
here's a firefox extension which might do what you're talking about - just right-click on the page and select 'create Deskcut'. it puts a link on your desktop which will open with your default browser.
[https://addons.mozilla.org/firefox/66/](https://addons.mozilla.org/firefox/66/)

you can do the same for links on a page too.

---

### Post by tturrisi on 2006-10-24
> **james_san said:**
> Well that's quite a silly answer really. .dll and .exe files are native binary files that require the win32 api. .url files are a simple text file.

There is no reason why this type of link couldn't be handled under linux, it is a very basic file format. One way to do it would be for firefox to handle a link like this, by recognising it and opening the url. Then gnome could associate .url files with firefox.

Another way would be for gnome (specifically nautilus - the file browser) to understand the .url file as a link, and open it in the default web browser (probably better, but could be messy since as far as I know it would be the only other link-file-type apart from .desktop)

Perhaps you could ask this question to the gnome developers? Like I said, it wouldn't be very hard to do...

Understood, & I agree.  I should have been more clear than to use .exe & .dll as examples.

I have researched this subject a bit and concluded that the .URL (Internet Shortcut) IS a microsoft filetype.  It is proprietary, just as a Norton Ghost image (.GHO) or a Nero image (.NRG) is proprietary.

Browsers made for Windows are not bound to free software licenses and they also are coded to use Windows APIs.

An Internet Shortcut is more than just a text file using .INI format.  Windows has a shell handler for the filetype .URL.  .INI format is a format with varying standards.

While Nautilus and Firefox probably could be made to handle Windows .URL files, there is really no need to do so.  AFAIK, linux Firefox can't Import IE Favorites (.URL files) but it can import IE exported Favorites in the form of an html doc.  (this I have not tested as I always have imported using an exported html doc)

So...this question of "why don't Windows .URL shortcuts work?" is kind of like asking "how come I can't open a saved Nero project in GnomeBaker?".  The answer is simply, "the filetype is not natively supported".

---

### Post by bsmith1051 on 2006-10-25
wow, you'd think I was asking for the moon or something!  My points here are:

1. Ubuntu and/or Gnome are correctly recognizing .URL file extensions as Microsoft Internet shortcuts ("x-mswinurl")

2. Ubuntu and/or Gnome are incorrectly handling them.

3. Microsoft .URL files are simple text files in which everything but the actual URL can effectively be ignored.

So I really fail to see why everyone is acting like this shouldn't be fixed.  It's an existing function which does not work!

---

### Post by tturrisi on 2006-10-25
> 1. Ubuntu and/or Gnome are correctly recognizing .URL file extensions as Microsoft Internet shortcuts ("x-mswinurl")

2. Ubuntu and/or Gnome are incorrectly handling them.

3. Microsoft .URL files are simple text files in which everything but the actual URL can effectively be ignored.

So I really fail to see why everyone is acting like this shouldn't be fixed. It's an existing function which does not work!

1. just cause a file type is recognized does not mean it should be able to be used.  Linux can recognize the Windows desktop.ini files but does not use them for anything.  The "file type" info is in the headers of the file and they get read & displayed in the properties dialog.  I have files on a fat partition made with a web editor that uses the extension .CPG.  Linusx displays the correct properties for this file type but these files cannot be used in linux unless the program that created them is installed-run under Wine.  The program that creates .URL files is Microsoft Internet Explorer.  Outlook & other MS products also craete .URL files but the are "hooked into" and utilize Internet Explorer APIs.

2. not necessarily so.  That a file cannot be handled the way Windows handles the file does not mean that it is incorrectly handled.

3. They are MORE than just simple text files!  What you see if open in a txt editor is .INI formatted text.  But have you looked at the file headers?  Other binary data?  There's more there than just 100+ bytes of text characters.

4. How is it an existing function that is broken?

I am NOT attempting to "make you wrong" or to prove that I know best or anything else like that.  This is a very interesting topic, so I read a lot via google about it.  I wanted to find out why my Firefox won't open MS shortcuts too.  I am satisfied with what I found out so far.

I ran into a similar issue years ago when I had failed to export my IE Favorites as an .HTM file and tried to import the .URL Favorites in a linux desktop.  I ended up copying the Favorites dir to another Windoes box and exporting the .HTM file.  I also stopped using Internet shortcuts period (.URL files), mostly cause I always disable any Active Desktop stuff on Win operating systems. And as well on linux I don't create shortcuts to web pages.

This issue of .URLs is not new.  This guy handles it this way:

Nsurl  [http://leuksman.com/pages/Linux](http://leuksman.com/pages/Linux)

"Nsurl is a little program I hacked together to read Internet Shortcut (.url) files such as are produced by Microsoft Internet Explorer and open the URLs they point to in *nix versions of Netscape Navigator. Useful for the ex-Windows user who hasn't yet copied his/her old "Favorites" into the Netscape bookmark file, or the minority *nix user in a Windows network where Internet Shortcuts abound. Download it here ([http://leuksman.com/linux/nsurl-0.2.tar.gz](http://leuksman.com/linux/nsurl-0.2.tar.gz)) (New version 0.2 written in Perl!)."

---

### Post by bsmith1051 on 2006-10-26
Thank you for the considered response.  I agree with you about point #1, i.e., just because Linux recognizes a file-type doesn't mean that it needs to support it.

I would still disagree with you, however, about point #3.  It seems like a trivial matter to scan a 'x/mswinurl' file for the "URL=" information and then treat this as a "Linux-style" Internet link.

---

### Post by roazena on 2006-11-01
> **tturrisi said:**
> 
3. They are MORE than just simple text files!  What you see if open in a txt editor is .INI formatted text.  But have you looked at the file headers?  Other binary data?  There's more there than just 100+ bytes of text characters.


If I go into a Windows shell and rename ub.URL to ub.obj and open it in TextPad, I get nothing more than the same ASCII characters that I would have gotten had I renamed it to ub.txt. No headers as far as I can see. TextPad seems to think it's straight ANSI/PC encoding.

If I go into TextPad and type from scratch
```
[InternetShortcut]
URL=http://ubuntuforums.org
```

and save it as ubuntu.URL, it immediately becomes a valid internet shortcut recognized by Windows. 

The .LNK file format is binary. The .URL file format is not. I suspect there's something fishy about the encoding that throws gedit, but the data itself is simple. 

Proof of the pudding is in the eating:
[http://www.aims.ac.za/pipermail/aims-tech/2006-October/000779.html](http://www.aims.ac.za/pipermail/aims-tech/2006-October/000779.html)

---

### Post by xodus1 on 2006-11-01
why bother just open up in text editor to show the full URL addy
copy and paste it to linux firefox address bar and save it in your favorite or drag it to your desktop
and vise/versa to windows

---

### Post by roazena on 2006-11-02
> **xodus1 said:**
> why bother just open up in text editor to show the full URL addy
copy and paste it to linux firefox address bar and save it in your favorite or drag it to your desktop
and vise/versa to windows

](*,)  Yes, that makes much more sense than enabling Linux to do the same thing with .URL files that Windows *AND* OS X already do.

---

### Post by lazyart on 2006-11-02
It's a matter of convenience, regardless of format... ie, we can open .xls, .doc files in OOo, so why not url files in a browser?

There is a similar discussion going on with PuppyLinux: [http://www.murga.org/~puppy/viewtopic.php?p=75921#75921](http://www.murga.org/~puppy/viewtopic.php?p=75921#75921)

Where are the mime handlers defined? It shouldn't be too hard to adapt that script...

---

### Post by bsmith1051 on 2006-11-02
> **xodus1 said:**
> why bother just open up in text editor to show the full URL addy
Because I can't, the Ubuntu/Gnome text editor throws an error about file-type.  I explained this in more detail in an earlier comment.

---

### Post by lazyart on 2006-11-02
I've got the regexp to do this... however grep won't cut it.  I'll make a perl script I guess, though I've never written a lick of Perl.  Perhaps I'll have time tomorrow evening to bang it out.

---

### Post by K.Morgan on 2007-11-14
Am i right in guessing after reading this thread that Windows and Mac internet shortcuts wont work in Ubuntu??

If this is true why?  I though an internet shortcut was an internet shortcut, why would an internet shortcut work in Windows and a Mac and vice versa but not in Ubuntu.

Does this mean it works the other way round also?  Meaning if i was to create an internet shortcut in Ubuntu it would not work in Windows or a Mac?

This is a very important issue for me and will probably be the deciding factor in switching to Ubuntu as i am constantly using different operating systems, and being able to use my internet shortcuts in all 3 is a must have.

Any suggestions?

Thanks

Kristian

---

### Post by oomingmak on 2007-11-15
[SIZE=3][SIZE=2]Windows URL internet shortcut files [/SIZE]**[SIZE=4]do[/SIZE] **[SIZE=2]work in Ubuntu[/SIZE] [SIZE=2](if you know how to correctly configure the system).[/SIZE][/SIZE]
[SIZE=3]
[SIZE=2] See my step-by-step[/SIZE] "**How To**" [SIZE=2]guide here:[/SIZE][/SIZE]

[SIZE=2][[COLOR=DarkOrange]**http://ubuntuforums.org/showthread.php?t=495131**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=495131&highlight=mswinurl")
[/SIZE] 
I don't know anything about Macs, so I can't help you there.

---

### Post by bsmith1051 on 2007-11-15
nevermind Windows shortcuts, why don't Firefox shortcuts work either?  If you drag-and-drop the URL to the desktop it'll create a shortcut labeled "Link to Web-site title".  But If you double-click on this 'shortcut' file, it opens in Text Editor.  If you drag-and-drop it into a Firefox window, it'll prompt you to open it in either Text Editor or Firefox, and if you choose Firefox it displays the text contents rather than using the link.  There's no way to re-use it except to go into it's properties, switch to the Link tab, copy the URL to the clipboard, and then go paste it into Firefox ... in other words, it's all manual.  

I'm really surprised that neither type of shortcut works automatically, even in Ubuntu 7.10.

---

### Post by oomingmak on 2007-11-16
That sounds like you may have some kind of file-type association issue. I'd check your MIME types list to see how it's being handled.

I've not had much problem with opening links that were dragged directly from Firefox in Ubuntu, apart from the odd instance where some weird character or symbol (that was used on the site) ended up in the file name causing it not to open when clicked on. Other than that they've worked fine for me.

I tend to install the [[COLOR=DarkOrange]**DeskCut**[/COLOR]]("http://deskcut.mozdev.org/") extension as an alternative to drag and drop in Firefox on Linux, but Deskcut is nowhere near as good as 'Create Shortcut'. Unfortunately Create Shortcut only works on Firefox for Windows.

---

