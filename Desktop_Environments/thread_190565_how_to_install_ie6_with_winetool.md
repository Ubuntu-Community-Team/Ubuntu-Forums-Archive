---
title: "how to install ie6 with winetool?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by forbmj on 2006-06-06
couldn't install ie6 successfully using the latest winetool. It seems iesetup.exe couldn't connect the MS server to get all the files needed. any help?

---

### Post by eeclark on 2006-06-06
[http://www.broomeman.com/support/wsiedown.html]("http://www.broomeman.com/support/wsiedown.html")

check out that site it should help at least get the files...

I had to do that when fixing someones Win98SE machine with no internet conn.  Had to use my machine to download the files and then burned a CD with them.

GL

---

### Post by Emx on 2006-06-06
Try [http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)

It should help...

---

### Post by eeclark on 2006-06-06
Keep in mind that the above post directing you to patrick.spacesurfer.com was tested on RH9 with wine-20030618. 

The older wine installations will have created a configuration file in:
~/.wine/config

The newest wine install (Wine 0.9.14) does not have the .config nor does it need it.

You may need to create the config file yourself but I do not know what the repercussions are.

---

### Post by forbmj on 2006-06-06
yes, following this instruction, I create a new config file. Then the winetool works for the ie6 installation.

Many thanks!


[QUOTE=Emx]Try [http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)

It should help...[/QUOTE]

---

### Post by mrtrick on 2006-06-06
For future searches, I've used [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html") very successfully on both Breezy and Dapper.

---

### Post by arizonagroovejet on 2006-06-06
[QUOTE=mrtrick]For future searches, I've used [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html") very successfully on both Breezy and Dapper.[/QUOTE]

I second this recommendation. I only found it today (not from here) and have used it to install IE6 on two dapper machines with no problems. Install the wine and cabextract packages from the universe repo, download ies4linux, unpack it and run. Simple as that.
The font rendering  kinda sucks but then it kinda sucks in a proper IE/Windoes install too :)
I only want it for web page checking/debugging purposes and it's good enough for that. Unlike the install of IE6 I had under Fedora Core done with the Wine-Config-Sidenet script, this one also pops up the proper script error messages.

---

### Post by eeclark on 2006-06-06
just curious why anyone would actually wnat to install IE anyway?
Can't you install Opera and use IE settings?

---

### Post by kaamos on 2006-06-06
[QUOTE=eeclark]just curious why anyone would actually wnat to install IE anyway?
Can't you install Opera and use IE settings?[/QUOTE]

Won't help if you are a web developer and want to test your site against the numerous ie bugs such as [this](http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug).

---

### Post by ubnoobie on 2006-06-06
[QUOTE=mrtrick]For future searches, I've used [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html") very successfully on both Breezy and Dapper.[/QUOTE]
same here -- easier to install with this than in windows itself  ;P

---

### Post by Kilz on 2006-06-06
[QUOTE=eeclark]just curious why anyone would actually wnat to install IE anyway?
Can't you install Opera and use IE settings?[/QUOTE]
Another option since a lot of people want to install IE to get flash 8 is install the Windoz version of Firefox with wine. It will allow the use of most plugins, but is infinitely safer than IE.
But to give you one example, I was hurt at work, the web site I have to go to find out if my checks are coming will not work with anything but IE, and I mean nothing else. I do have IE installed, but I only go to that one site, no others. What some people don't understand is that IE is a total security risk even running it under wine. Surfing with it is a BIG no no.

---

### Post by arizonagroovejet on 2006-06-06
[QUOTE=eeclark]just curious why anyone would actually wnat to install IE anyway?[/QUOTE]

Because of all modern web browsers IE is both the most used and the poorest at conforming to and supporting W3C standards for HTML and CSS. It is quite easy to create a web page which uses completely valid HTML and CSS and find that whilst Firefox, Mozilla, Konqueror, Safari and Opera all render that page in the same way, IE displays it differently because of some quirk in it's HTML or CSS implementation  or because it turns out not to support some bit of CSS you used which every other browser does support. (Like the > child selector for example.)

There are also scripting methods unique to IE. For example the XMLHTTPRequest method which is what makes AJAX possible is implemented using ActiveX in IE but since that's unique to IE/Win, Firefox etc use a different method. So you need to check things like that specifically in IE. (XMLHTTPRequest is actually an MS invention, shame they implemented it in ActiveX and thus ensured that IE does it differently to every other browser.)

IE can be a real pain in the *** when it comes to creating websites. 

[QUOTE=eeclark]Can't you install Opera and use IE settings?[/QUOTE]

That makes Opera identify itself as being Internet Explorer by altering the values of navigator.useragent and similar to the ones used by IE. (Though Opera leaves the word Opera in the string.) This will fool some sites with badly written browser detection scripts(*) in to thinking you are using IE and let you use them when they may other wise block you.
What it doesn't do is make Opera render pages as IE would so you can't use it to check for things like I mentioned above.

(*) browser detection by looking at navigator.useragent and simliar is quite commonly used but is completely flawed because many browsers let you alter the values.

On a completely unrelated topic - where's the spall chucker in these forums?

And why is the word a s s censored? a s s.  a s s. bottom!

---

### Post by msak007 on 2006-06-06
I installed IE under Wine using [WineTools]("http://www.von-thadden.de/Joachim/WineTools/"). I know some people don't like this option, but WineTools really is useful if you want to install more than just IE. Just a word of caution though, it doesn't work with the version of Wine in the default Dapper repositories (installation of IE always crashes). To get it to work, add ```
deb http://wine.budgetdedicated.com/apt dapper main
``` to your sources, then update and fetch the upgrade. Once that's done, WineTools will install IE with no problem.

EDIT: Sorry after going back and reading the initial post, I realized you were trying to use WineTools to begin with. I had an issue where it wouldn't download once (in Breezy I think), and download the entire IE package for offline installation. But even that wouldn't work with this version of Wine, so either way an upgrade was needed.

---

