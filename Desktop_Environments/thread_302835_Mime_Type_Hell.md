---
title: "Mime Type Hell"
date: 2006-11-19
forum: Desktop Environments
---

### Post by Quietlife on 2006-11-19
Hi,

(Ubuntu 6.06.1 LTS Std Gnome Desktop)
(Problem exists in multiple installs and is not hardware specific)

Could anyone please direct me to instructions on how to disable the automatic typing of files by their content ?

I would really like to do this as I hate being called a liar by gnome !

Example :

use a text editor and paste the following into a new text file called foxme.txt
<HEAD>
THIS IS A TEXT FILE
</HEAD>

Now double click on our text editor created text file - what does it open in ?

As a text file with a txt extension I would expect to see a text editor - not a web browser, yet there it is in Firefox !!

Worse if I change the application use to launch "foxme.txt" it also changes it for ALL files that "look" like HTML.

PLEASE PLEASE PLEASE Would someone tell me how to make it do what the extension says rather than guessing and in the process calling me a liar ?

Thanks in advance 

Matt

---

### Post by temcat on 2006-11-19
The problem that hit you is called "MIME sniffing". I quickly googled for a solution for Nautilus, but haven't found anything other than complaints similar to yours (BTW, Internet Explorer 6.0 has this problem, too!). I believe this is hardcoded in Nautilus and unfortunately cannot be turned off. Still, I may be mistaken.

---

### Post by mannheim on 2006-11-19
This is not a complete solution, but you can tweak the rules the gnome uses when to decide mime types from the sniffed contents. See the section on mime types in [http://http://www.gnome.org/learn/admin-guide/latest/]("http://http://www.gnome.org/learn/admin-guide/latest/")

You want to creat/edit a file /usr/share/mime/packages/Overrides.xml

For example, there may be a rule that says that any file containing "<HEAD>" is an html file. If so, then you can override that rule.

---

### Post by CatKiller on 2006-11-19
You can right-click to select which application you'd like it to open in. And the icon changes based on which MIME type Gnome thinks the file is, so it's not like you can pretend that you didn't know.

File type identification based solely on the filename is lame.

---

### Post by Quietlife on 2006-11-19
Hi Thanks for the info so far .....

Whilst I understand that this is not some peoples choice, this is my system and I'd like it to do what I tell it not re-write the rules to suit it's own ends !

Furthermore this removes the protection that is provided by Thunderbird's "defanging" (renaming) of files. (an executable will be an executable regardless of it's file name).

Identification based *solely* on content is worse than useless UNLESS it can tell the difference between a text file and html page (which it cannot).

The sample I provided is most certainly a text file - I created one myself with pico to confirm that it cannot tell the difference.

With the sample you can tell it to choose gedit to open with and lo and behold it opens in gedit.

But wait what happens when I now double click a true ".html" file - does it open a webbrowser ?  

NO

It opens the html file in gedit !!!

My idea of a solution would be  :

Lookup filename extension - is there an existing application map ?
Yes - use the map, but add options to "open with" based on the mime info just in case the filename is incorrect.
No - Use the mime info directly to try to open the file. 

This way I could map ".txt" to gedit *without* tying ".html" as well.

I think this is possible but requires a better understanding of the methods for updating the mime database stored and used by gnome.

Any help greatfully recieved.

T.I.A.

Matt

P.S.

mannheim - I'm very interested in this, but the link seems to take me to [http://www.w3.org/Protocols/](http://www.w3.org/Protocols/) and I cannot seem to find the "mime types" section ?


UPDATE :

[http://rox.sourceforge.net/desktop/MIME-Editor](http://rox.sourceforge.net/desktop/MIME-Editor)

This at least shows me what it is doing, but as the "text/html" mime type is "provided by system packages and connot be edited or deleted" I cannot alter it :(  

Any ideas ?

---

### Post by CatKiller on 2006-11-19
> **Quietlife said:**
> The sample I provided is most certainly a text file - I created one myself with pico to confirm that it cannot tell the difference.

With the sample you can tell it to choose gedit to open with and lo and behold it opens in gedit.

But wait what happens when I now double click a true ".html" file - does it open a webbrowser ?

And shell scripts and python programs and... oh yes, web pages, are all text files that you can create in pico. What's the point?

I don't really see why you're complaining about things that you yourself are doing. You're deliberately setting all files of type HTML to open in gedit, and then complaining about the fact that all files of type HTML open in gedit. Perhaps a more sensible option would be to set HTML files to open in a browser, if that's what you want, and then when you see a file with a .txt extension but a HTML icon you can think "ah, yes, this is a file that I've malformed myself - I think I'll right-click on this file and open it in gedit, since that's what I'd seem to like to happen".

Perhaps some [more reading]("http://arstechnica.com/reviews/os/metadata.ars/") will give you a different perspective.

---

### Post by Quietlife on 2006-11-20
I reitterate that this is my system and it is not working the way I want it to.

I am creating a text file.

**It may LOOK like a html file but it is not.**

The mime system looks at my file and

DECIDES FOR ITSELF THAT IT IS HTML

**There is no easy way to tell the system that it is not to be treated as html**, it has made up it's mind based ***SOLELY*** on it's content - ignoring the only thing that I can change about the file - it's name/extension - not at all flexible !

Just because it looks like a html file does not necessarily mean that it IS a html file or that I want it treated as such!

I cannot change how I open this file without also changing **ALL** files that **LOOK TO THE SYSTEM** like html.


The "I'll right click" is what I've been doing since I converted from MS/.net/C# development to Ubuntu/Mono/Monodevelop/C# (3 months live with 2 years prior "playing" with different distros) and it's incredibly tiresome in a day on day scenario - including the additional RSI.

---

### Post by CatKiller on 2006-11-20
> **Quietlife said:**
> I cannot change how I open this file without also changing **ALL** files that **LOOK TO THE SYSTEM** like html.

That's just not true. 

Right-click on the file
Select Open with Other Application
Select whatever you want
(I suspect you've already done these steps)

If you find that all the files are being opened by the wrong application, right-click -> Properties -> Open With -> put the radio button in the application you'd like as the default.

So for a proper HTML file, you double-click. Count them - two clicks. For your munged together malformed file that looks like a HTML file but isn't, you right-click, move the mouse over Open With -> Text Editor and left click. Count them - two clicks. Oh, but you have to, like, move the mouse! zomg teh RSI :roll:

Using a mouse doesn't take much skill, but it does take some, I suppose. Do you also wonder why clicking on the Terminal launcher doesn't automatically open your email client?

If you don't like the "human interface" decisions that the Gnome people have made, you are perfectly free to choose a different desktop environment. Or make a new one.

---

### Post by Quietlife on 2006-11-20
> **CatKiller said:**
> That's just not true. 

Right-click on the file
Select Open with Other Application
Select whatever you want
(I suspect you've already done these steps)

If you find that all the files are being opened by the wrong application, right-click -> Properties -> Open With -> put the radio button in the application you'd like as the default.

So for a proper HTML file, you double-click. Count them - two clicks. For your munged together malformed file that looks like a HTML file but isn't, you right-click, move the mouse over Open With -> Text Editor and left click. Count them - two clicks. Oh, but you have to, like, move the mouse! zomg teh RSI :roll:

Using a mouse doesn't take much skill, but it does take some, I suppose. Do you also wonder why clicking on the Terminal launcher doesn't automatically open your email client?

If you don't like the "human interface" decisions that the Gnome people have made, you are perfectly free to choose a different desktop environment. Or make a new one.

I thank you for your time however -

Once or twice a day - right click - fine.

Now do it 4 or 5 times every 10 minutes...................

(I am dealing with data files from an old DOS app that gnome constantly mis-recognises - not necessarily as html that is just an example)

Why should I put up with this annoyance when the gnome subsystem can cater to my needs ?

It is in fact DESIGNED to be flexible - there is simply no easy user interface to make the required changes.

Hence I ask for help.

I have subsequently found that :

/usr/share/mime/packages/freedesktop.org.xml

Seems to contain the the backbone of the mime type database as described here :

[http://www.gnome.org/learn/admin-guide/latest/mimetypes-source-xml.html](http://www.gnome.org/learn/admin-guide/latest/mimetypes-source-xml.html)

I am not asking it to do anything it cannot manage.

The change I need does NOT require new code or extra features this is standard gnome functionality.

I now think that all I need to know that that is in fact the file I need to and how to update the mime database after I edit it.

The whole beauty of open source is that you can shape it any way you want - I'm simply asking for help in achieving MY preferred setup I'm not asking for it to apply to anyone except myself.

YMMV

---

### Post by hpp3 on 2007-02-06
you can set preferences for text/html files by extension in the /usr/share/mime-info file and then sync it with your .desktop shortcuts in /usr/share/applications/defaults.list

more info here:
[http://wings.buffalo.edu/computing/ublinux/HOWTO-Mailcap.php](http://wings.buffalo.edu/computing/ublinux/HOWTO-Mailcap.php)

(despite the topic named, it doesn't just apply to Mailcap, but mimetypes in general that are no longer handled by calls from /etc/mime.types)

"Mime sniffing" has been a defining feature of Unix from the beginning and really is a wonderful thing, but I do agree there *has* to be a way to differentiate when the content is the same type. Hopefully this works for you...

---

