---
title: "Why don't file types point to a folder?"
date: 2012-06-04
forum: Desktop Environments
---

### Post by Stray Wolf on 2012-06-04
Hope the title isn't misleading. Maybe I can change it if someone gives me a better wording.

When downloading a certain file, you get an prompt to "open with" or "save" to file. So, depending on the file type, is there a way for selecting "save" to automatically open to the corresponding folder? Video files open to save in the video folder, music to music, documents to documents etc...

---

### Post by Frogs Hair on 2012-06-04
The browsers I have used only offer save to downloads or ask every time . I haven't seen an option to move a package type  automatically  to a folder other than downloads.

A compressed package may include different types of content . Ubuntu can offer options to open a compressed package but can't screen the content prior to extraction and move it to a preferred folder.

The ask every time option allows the user to do the directory sorting.

---

### Post by 3Miro on 2012-06-04
This is a Browser feature. I was looking for this some time ago and there was a Firefox addon that supposedly did this, however, I never got it to work. Look for FF addons and what they do.

---

### Post by inashdeen on 2012-06-04
That's interesting. gonna say up and hope someone could respond to this :)

---

### Post by Stray Wolf on 2012-06-04
> **Frogs Hair said:**
> The browsers I have used only offer save to downloads or ask every time . I haven't seen an option to move a package type  automatically  to a folder other than downloads.

A compressed package may include different types of content . Ubuntu can offer options to open a compressed package but can't screen the content prior to extraction and move it to a preferred folder.

The ask every time option allows the user to do the directory sorting.

Well, I don't necessarily mean it has to save there automatically, but the corresponding folder to the file type should automatically be the first option when you select save. So for most instances you just click "okay". But then a drop down menu for other choices as it is now. IMHO

---

### Post by Frogs Hair on 2012-06-04
Music , photos , text documents , and so on can be compressed into a tar.gz or other type of compressed format. The computer recognizes the package and not what's compressed inside. The always ask option allows you to put the file where you want. You may know it is a music or video file but the computer doesn't while the package is compressed.

Save folder extension Firefox. [https://addons.mozilla.org/en-US/firefox/addon/automatic-save-folder/](https://addons.mozilla.org/en-US/firefox/addon/automatic-save-folder/)

---

### Post by Stray Wolf on 2012-06-06
> **Frogs Hair said:**
> Music , photos , text documents , and so on can be compressed into a tar.gz or other type of compressed format. The computer recognizes the package and not what's compressed inside. The always ask option allows you to put the file where you want. You may know it is a music or video file but the computer doesn't while the package is compressed.

Save folder extension Firefox. [https://addons.mozilla.org/en-US/firefox/addon/automatic-save-folder/](https://addons.mozilla.org/en-US/firefox/addon/automatic-save-folder/)

Understood. People download all sorts of files types. I was just stating what I thought would be intuitive. Yes, "always ask" let's you decide. But what would be wrong with the first option being based upon the file type? For tar.gz I'd expect it to be "Downloads". So you could just click ok. But if you want it somewhere else you just select where. And it would be nice for the Archive Manager's "Extract to" option to feature something similar as well. Really, it could use Zeitgeist to get a feel for where you put what.

---

### Post by Frogs Hair on 2012-06-06
It might a nice feature in the archive manager , but I would have to educate myself as ti why it hasn't been done.  If I were to send a compressed package with an audio file , a picture and a pdf document how could the archive manager intuitively know what directory I wanted to put the contents in ?

As it is now it is possible to navigate to a sub-folder and I do this often with pictures. If a photo was routed to pictures I would still have move it to the folder of my choice. GTK themes sometimes include a backgrounds and these are unusable unless the package is extracted and  and the photo moved to a directory where it can be used as a desktop background. 

There is large number of compressed  package types and and a picture or audio file for example can be placed into a folder compressed into an rar, tar.gz, zip , 7zip and so on.

The type used depends on the preference of the person doing packaging so routing to a directory based on package type would not be very helpful.

---

### Post by Stray Wolf on 2012-06-06
> **Frogs Hair said:**
> It might a nice feature in the archive manager , but I would have to educate myself as ti why it hasn't been done.  If I were to send a compressed package with an audio file , a picture and a pdf document how could the archive manager intuitively know what directory I wanted to put the contents in ?

As it is now it is possible to navigate to a sub-folder and I do this often with pictures. If a photo was routed to pictures I would still have move it to the folder of my choice. GTK themes sometimes include a backgrounds and these are unusable unless the package is extracted and  and the photo moved to a directory where it can be used as a desktop background. 

There is large number of compressed  package types and and a picture or audio file for example can be placed into a folder compressed into an rar, tar.gz, zip , 7zip and so on.

The type used depends on the preference of the person doing packaging so routing to a directory based on package type would not be very helpful.

It just seems that since all computers, regardless of the OS, have the same folder categories (Pictures, Music, Documents, Videos, Downloads) then all computer users frequently obtain and manage files of these types. I'm not trying to say navigation should be changed at all. I'm just saying the first option should correspond with the file type. I thought I was coming up with something intuitive. Most tar.gz that have multiple file types are for installation anyway and include an install script which extracts everything to where it is supposed to be. But as it is now the "always ask" function always starts the navigation at the "Downloads" folder. But if a file is obviously a music file, there's no reason why navigation shouldn't start in the "Music" folder. It's not a big deal, but it's a small convenience that adds to the whole.

If you were to send me a compressed file that included an audio file , a picture and a pdf document, I'd hope they all have something to do with one and other in some way. If this is the concoction of file types that usually goes into an Impress document, and Zeitgeist knows I save similar file concoctions into "Documents", then "Documents" should be where the navigation starts in the "Save" or "Extract to" menu.

---

### Post by Frogs Hair on 2012-06-06
A music file would have to be extracted from the compressed package in order for it to Identified as such . Where would this take place ?  

 Zeitgeist collects information over time and if you were to change the routing of a file to another  directory  Zeitgeist would continue route to the old location based on history until a new pattern was established . If The history was cleared routing information for to other directories would be lost.  Granted it were possible to even use  Zeitgeist in this way.

There are some users that are opposed  to the use of Zeitgeist at all and prefer to be able to have control over what their computer does and remembers about their usage habbits . Some actually disable it . If have three files to send I send them in one package .

---

### Post by Stray Wolf on 2012-06-08
> **Frogs Hair said:**
> A music file would have to be extracted from the compressed package in order for it to Identified as such . Where would this take place ?  

 Zeitgeist collects information over time and if you were to change the routing of a file to another  directory  Zeitgeist would continue route to the old location based on history until a new pattern was established . If The history was cleared routing information for to other directories would be lost.  Granted it were possible to even use  Zeitgeist in this way.

There are some users that are opposed  to the use of Zeitgeist at all and prefer to be able to have control over what their computer does and remembers about their usage habbits . Some actually disable it . If have three files to send I send them in one package .
Thanks for your patience. I was just hoping to have a helpful suggestion really.

---

