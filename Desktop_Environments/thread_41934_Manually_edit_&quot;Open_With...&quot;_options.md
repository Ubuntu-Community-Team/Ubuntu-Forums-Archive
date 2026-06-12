---
title: "Manually edit &quot;Open With...&quot; options?"
date: 2005-06-15
forum: Desktop Environments
---

### Post by uc50_ic4more on 2005-06-15
Hello, everyone!

1) Is there a way to specify (or more accurately, *change*) a default application for any given file type? For example, currently my Rich Text .rtf file are bound and determined to open in gedit. AbiWord is avilable by right-clicking and choosing "Open With...", but I'd like AbiWord to be default.

2) In the same example above, I have Scribus listed twice in the "Open With..." menu for .rtf. .htm files open in gedit by default as well, and Firefox is listed twice in the "Open With..." menu... I'd like to clean this stuff up a bit.

I have looked in every file I can get my hands on in my filesystem that has MIME in the title, and by gum I cannot find a master file that contains all of the "Open With..." info.

Thank you!

---

### Post by netrattler on 2005-06-15
All you need to do is right click on the file, click on Properties, click on the Open With tab, click on the add button to add the aplication you want to use, and select the application you want to use by default by making sure the circle is filled in by it. Click on the Close button and test it out. Now the application you want to start it with will open those files from now on.

Joe

---

### Post by uc50_ic4more on 2005-06-17
[QUOTE=netrattler]All you need to do is right click on the file, click on Properties, click on the Open With tab, click on the add button to add the aplication you want to use, and select the application you want to use by default by making sure the circle is filled in by it. Click on the Close button and test it out. Now the application you want to start it with will open those files from now on.

Joe[/QUOTE]

Joe, thank you for your indulgence - I cannot *believe* that escaped me!  ](*,)

---

### Post by bobby555 on 2005-06-17
This doesn't always work for all file types.. When trying to use VLC as the default application for opening .ogg files (theora video) I get some kind of error message.. '..not supported' or something like that (not on my ubuntu machine right now). Is there a way of forcing this as VLC does play the ogg file when opened from within VLC?

AM

---

### Post by iomicifikko on 2005-06-17
yes, that happens to me too, on a few ubuntu installations, i dunno why.

the more or less exact message is (translated) :  the application cannot be saved/added(?)n to the application database

any idea?

byez

---

### Post by gavd on 2005-09-12
[QUOTE=iomicifikko]yes, that happens to me too, on a few ubuntu installations, i dunno why.

the more or less exact message is (translated) :  the application cannot be saved/added(?)n to the application database

any idea?

byez[/QUOTE]

I just installed the preview of breezy badger and I'm getting this error with VLC. When i open it manually and drag a video file in it works perfectly but it says It can't be added to the application database to open as default.

Any ideas?

---

### Post by blackant on 2005-09-12
hehehe, I was about to post a topic on this issue..
when I found this thread.

It solved my problem as I have 2 x 'open with firefox' for html files. ](*,)

---

### Post by brian g on 2005-09-16
[QUOTE=bobby555]This doesn't always work for all file types.. When trying to use VLC as the default application for opening .ogg files (theora video) I get some kind of error message.. '..not supported' or something like that (not on my ubuntu machine right now). Is there a way of forcing this as VLC does play the ogg file when opened from within VLC?

AM[/QUOTE]
-right click on an .ogg file
-go to properties
-you may get an error or 2 here.. close the first error box first.. than the second one if you do
-go to "open with" tab
-click add
-click the triangle next to use custom command
-change xwvlc to vlc
-click add
-close properties box

---

