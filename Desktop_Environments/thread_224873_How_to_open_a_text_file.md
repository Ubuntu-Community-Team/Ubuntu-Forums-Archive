---
title: "How to open a text file?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Luke771 on 2006-07-28
I dual boot Ubuntu and WinXP each has its dedicated partition, and a third bigger partition is used as file storage for both OSs (with Ext2 and Ext2 Win drivers)

My problem is that I often write a file in Linux that I want to be able to see in Windows as well. When it's text files, i simply add .txt at the end of the file name so windows will open them with Notepad by default, but when I open in Notepad a text file that I created in Gedit, all the braks are gone, word come after each other as in one long paragraph written without hitting enter. In addiction, I see a lot of small squared "thingies" between one word and the next one.

Text file created in Notepad looks exactly the same in Gedit, but files created in Gedit, or other linux text files, look funny whan opened in Notepad under Windows.

An example, this happened a couple of days ago: I tried to open the Linux Priovoxy configutation file under Windows with Notepad because I wanted to copy some lines to the Windows Privoxy configuration, but that was very difficult to do because the layout of the text was all messed up: no line breaks, and those squared thingies everywhere.

Is it possible to write text files in Linux in a way that Notepad can read properly?
Or should I use an alternative Windows text editor?
Anybody know which text editor for windows is 100% compatible with files created in Linux?

---

### Post by jordilin on 2006-07-28
Perhaps using some kde editor like kate enables writing documents for m$ win style. If I'm not wrong unix text files differ from m$ win text files in the way they manage the end of line \n.

---

### Post by 5-HT on 2006-07-28
vi/vim can open/save in dos and unix formats (and more! Type *:help ffs *for info), and I believe nedit as well.

For information on why you are experiencing the issue: [http://en.wikipedia.org/wiki/CRLF](http://en.wikipedia.org/wiki/CRLF).

Also, there is a great utility that automagically converts text files to and from dos and unix formats called tofrodos (available in the repos and also for windows). 

HTH

---

### Post by Luke771 on 2006-07-28
Thanks.

---

### Post by tturrisi on 2006-07-28
Windows Notepad is NOT a standard basic text editor and cannot usually display tabs and other formatting created by other txt editors.  In windows, I use a great free txt editor called WIN32PAD.  It has a lot of features including line numbers, can save fies as many different txt formats like .bat, .cmd, .html, .php, and can save a file with no extension at all.  get it here:  [http://www.gena01.com/win32pad/](http://www.gena01.com/win32pad/)  No install needed, just unpack the zip & run.  Also can be downloaded w/ an installer.

---

### Post by msandersen on 2006-08-03
As noted above, the problem is that Microsoft uses a different standard for Newlines.
In Windows, I use [EditPad Pro]("http://www.editpadpro.com/"). The free 'lite' version is the same only doesn't have Contextual Hightlighting and such, which I wanted. Great text editor either way. Gedit has most of its functionality for free under Linux.
Of course, you could just use WordPad in Windows, which doesn't suffer from this problem.

If you need to write a text document that can be opened in NotePad, which doesn't understand Unix Newlines, the you can use **tofrodos**, as indicated, to convert it.
To get Gedit to convert text files to DOS format using Tofordos, see [this post]("http://www.ubuntuforums.org/showthread.php?p=1332033#post1332033").

---

### Post by bbzbryce on 2006-08-03
> **Luke771 said:**
> I dual boot Ubuntu and WinXP each has its dedicated partition, and a third bigger partition is used as file storage for both OSs (with Ext2 and Ext2 Win drivers)

My problem is that I often write a file in Linux that I want to be able to see in Windows as well. When it's text files, i simply add .txt at the end of the file name so windows will open them with Notepad by default, but when I open in Notepad a text file that I created in Gedit, all the braks are gone, word come after each other as in one long paragraph written without hitting enter. In addiction, I see a lot of small squared "thingies" between one word and the next one.

Text file created in Notepad looks exactly the same in Gedit, but files created in Gedit, or other linux text files, look funny whan opened in Notepad under Windows.

An example, this happened a couple of days ago: I tried to open the Linux Priovoxy configutation file under Windows with Notepad because I wanted to copy some lines to the Windows Privoxy configuration, but that was very difficult to do because the layout of the text was all messed up: no line breaks, and those squared thingies everywhere.

Is it possible to write text files in Linux in a way that Notepad can read properly?
Or should I use an alternative Windows text editor?
Anybody know which text editor for windows is 100% compatible with files created in Linux?

Open these files using wordpad in Windows.  It handles the \n (newline) properly which is what linux does by default.  If you then save it right after opening wordpad it will replace all \n with \r\n (windows newline).  Then you can open in notepad just fine.  Linux should have no problems with \r\n so you shouldn't see any extra line breaks.

---

### Post by nexu56 on 2007-08-05
Surely it would be trivial for someone techy enough to write a plugin for gEdit that allows you to select either Windows or Unix line breaks. 

Anyone? :)

---

### Post by jcr1 on 2008-04-02
I have just had the same issue. I created a html document in gedit, then I wanted to open it on another machine running windows, to do a bit more work so I assumed it would open in notepad. Same funny layout problem.

But opening in wordpad its fine, so long as any work i do to it can then be reopened back in gedit I'm happy with that. Otherwise I'll try that win32pad app.

Jon

---

