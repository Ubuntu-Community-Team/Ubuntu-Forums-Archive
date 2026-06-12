---
title: "Editing html files with OpenOffice doesn't work"
date: 2009-03-01
forum: Education &amp; Science
---

### Post by jaime256 on 2009-03-01
I'm trying to open an html file with open office, but the program just opens for a second, then crashes. Does anyone have any idea why you can't open an html file under OpenOffice. The file is stored in my nas and I just edit them from there. I just want a GUI interface to check the page changes. I can do most of the basic coding, but I still need a way to see the final page were I can also edit if I need to. This is the version that comes with Ubuntu 8.10.

---

### Post by rajan on 2009-03-01
version 2.0.2 works fine for me. have you tried upgrading/downgrading? when i open an html file it opens in "OpenOffice.org Writer/Web"

have you tried running open office from the terminal to see what errors pop up? it may be just a missing library.

---

### Post by jaime256 on 2009-03-02
Rajan, I haven't tried upgrading or downgrading anything yet. I did went a ahead and tried your suggestion on running it from the terminal, but first I tried just dragging the file from the share to the openoffice window and well, that didn't work. I then opened open office and got that stinking username and password prompt even though I had already logged into the share. Anyway, I put in my info, but still got the same result as before. It opens for a second, then I get the error telling me the file will be restored. Lastly, here's the output from the terminal:

I'm just doing a copy and paste. The forum is getting backed up so I can't upload any images. I'll post them torrow. Pretty much the same one as the first one above and a general error after I tried dragging the file.
-------------------------------------------------------------------------
jaime@:~$ openoffice
javaldx: Could not find a Java Runtime Environment! 
jaime@:~$ 
(soffice:8066): Gtk-WARNING **: Operation not supported by backend

(soffice:8066): Gtk-WARNING **: Operation not supported by backend

(soffice:8066): Gtk-WARNING **: Operation not supported by backend
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
connection_message_func(): Callback
CALLBACK: full-authentication!!!

(soffice:8066): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
connection_message_func(): Callback
CALLBACK: save-authentication!!!
connection_message_func(): Callback
CALLBACK: save-authentication!!!

** (soffice:8066): WARNING **: Input Stream exceptional result 'Internal error' (3)
terminate called after throwing an instance of 'com::sun::star::io::IOException'
jaime@:~$ 
------------------------------------------------------------------------
And you're right, Writer/Web is what I was hoping to get. No luck yet...I also just installed the Java 6 runtime since I noticed that came up, but I still get the same thing when I try to open the html file. This is the OpenOffice version that comes with Ubuntu 8.10.

> **rajan said:**
> version 2.0.2 works fine for me. have you tried upgrading/downgrading? when i open an html file it opens in "OpenOffice.org Writer/Web"

have you tried running open office from the terminal to see what errors pop up? it may be just a missing library.

---

### Post by gunksta on 2009-03-02
> **jaime256 said:**
> I'm trying to open an html file with open office, but the program just opens for a second, then crashes. Does anyone have any idea why you can't open an html file under OpenOffice. The file is stored in my nas and I just edit them from there. I just want a GUI interface to check the page changes. I can do most of the basic coding, but I still need a way to see the final page were I can also edit if I need to.


Here's a thought to narrow down exactly what the problem is. Copy the file to your local machine. Open it with OpenOffice. If it crashes, it will tell us that it has nothing to do with the file being on a remote server. If it works correctly, it means that the problem IS related to opening a remote file.

You could also try to upload a simple test document (word, calc, whatever) to the NAS. Create the file with OOo on your local machine. Upload to the NAS and try to open it again. If that crashes OOo, then we know for sure the problem is with opening files on the NAS.

---

### Post by jaime256 on 2009-03-02
Thanks for the suggestion. I totally forgot my basics this time. Okay, I just went ahead and copied the file locally and then it did get recovered locally, meaning it does open in writer after I copy it. So trying to open things up from the nas is doing something weird. I'm having a problem opening a regular document but after I have logged in then it works. The html file was the only one crashing openoffice though. I guess I will have to do a clean install sooner than later just to see if that fixes these things. Here are the previous messages too. But at least I can open the file now. Sometimes it helps to take a break. Thanks guys. 

Oh and just for the fun of it I still get this when I check the terminal output:
jaime@:~$ openoffice
javaldx: Could not find a Java Runtime Environment! 
jaime@:~$ 
(soffice:7900): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
jaime@:~$ 


> **gunksta said:**
> Here's a thought to narrow down exactly what the problem is. Copy the file to your local machine. Open it with OpenOffice. If it crashes, it will tell us that it has nothing to do with the file being on a remote server. If it works correctly, it means that the problem IS related to opening a remote file.

You could also try to upload a simple test document (word, calc, whatever) to the NAS. Create the file with OOo on your local machine. Upload to the NAS and try to open it again. If that crashes OOo, then we know for sure the problem is with opening files on the NAS.

---

### Post by rajan on 2009-03-02
> **jaime256 said:**
> 
Oh and just for the fun of it I still get this when I check the terminal output:
jaime@:~$ openoffice
javaldx: Could not find a Java Runtime Environment! 
jaime@:~$ 
(soffice:7900): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
jaime@:~$

I find it strange that there would be no change between the java error before installation of java and afterwards. it is possible that there isn't a proper link made between the installation you've made and the open office suite.

As you've probably surmised, this probably isn't the reason you were getting problems before while pulling files from the NAS. Neither is the warning you get later about the deprecation. 

it's very possible that this is a bug, and a quick google search showed a few cases where people had similar problems. just to make sure, i suggest you check your version (usually under Help>About OpenOffice.org), and search for information about it.

---

