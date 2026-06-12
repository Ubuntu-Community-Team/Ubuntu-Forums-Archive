---
title: "Associate Program to file extension problen. 12.04 &amp; Gnome"
date: 2012-08-04
forum: Desktop Environments
---

### Post by stephen67 on 2012-08-04
I want to use gPHPedit and I have installed it using the Ubuntu Software Center.

I am trying to associate my *.php files, but this program is not given as an option.

In Nautilus I right click on a php file, open properties, click on open with, click on show other applications, get a couple dozen, but gPHPedit is not one of them!

Any ideas on how I can make the association?

Thanks

---

### Post by ajgreeny on 2012-08-04
You need to right click on the file and use the Open With tab, and then add whatever the command is to start gPHPedit as a custom command (gphpedit?  I don't know what the command is but presumably you can find that easily enough).

---

### Post by OM55 on 2012-08-04
Another option - you can use Ubuntu Tweak (sudo apt-get install ubuntu-tweak) to set up exactly what applications will be included in the "Open with..." option, and which one will be the default one.

---

### Post by kornelix on 2012-08-05
This option does not seem to be available.
 + right click on some file in Nautilus
 + select "open with other application"
 + select "show other applications"
The only option at this point is "find applications online". I recall there used to be an option to enter a command line but this is not there. I am using 12.04.

---

### Post by OM55 on 2012-08-05
I already provided the solution in my previous reply, but I may have not been completely clear. So here it is, step by step:

The easy way would be to instal Ubuntu-Tweak and change the setting there.

1. To accomplish that go to: [http://ubuntu-tweak.com](http://ubuntu-tweak.com) and download the latest Ubuntu Tweak version (currently 0.7.2). To install just double click on the downloaded '.deb' file.

2. You can launch it from the menu (if not using Unity) or from the command line by typing:
 	Code:
 	ubuntu-tweak 
3. While in Ubuntu Tweak click on the "Admin" tab (at the top) and  then on "File Type Manager" (at the lower left). Then in categories  select "All" - After this last step it may seem as if Ubuntu Tweak  froze, but be patient, it is just collecting the data on all different  file types associations in your system. 

4. When the process is done you will see all file types sorted  alphabetically. Scroll down to find your specific file type. It may be  listed by the name of the association, not necessarily the file type.

5. Highlight the selection and click on the 'Edit' button (lower-right).  Then simply select from the list. Notice that there is no 'OK' button,  once you select the new file association the change has been made. 

6. If the desired application is not listed, click on the 'Add' button.  If the desired application is yet not listed in the list of available  additional applications, just select 'Command Line' and either type in  the file name of the desired application (it has to be in the search  list) or the full path to the binary file of the application. 

One way or the other, Ubuntu Tweak makes it very easy to change file type associations, as well as other little tweaks.

Hope that helps!

---

### Post by kornelix on 2012-08-05
OK thanks for the very thorough response.

Tweak does not list the file type I need, which is .RW2 

This is a Panasonic camera RAW file, which Nautilus knows about because that is what is written in the file type column. 

I was hoping to discover the secret place where file type to app associations are kept and update that file. No luck so far, having scoured both suitable locatioins, ~/.local/share/applications and /usr/share/applications. I tried imitating some of the entries I found there but this failed to work. 

This association was easy to change in prior releases of Ubuntu, but some developer nanny decided it was too complicated and removed it. Now there is a wave of compensating tools like ubuntu-tweak. 

Thanks, but I am still lost.

---

### Post by OM55 on 2012-08-05
> **kornelix said:**
> 

Tweak does not list the file type I need, which is .RW2 

This is a Panasonic camera RAW file, which Nautilus knows about because that is what is written in the file type column. 


As I explained is step (6) if the association is not listed, you can add it in Ubuntu Tweak:

> 
6. If the desired application is not listed, click on the 'Add' button.   If the desired application is yet not listed in the list of available   additional applications, just select 'Command Line' and either type in   the file name of the desired application (it has to be in the search   list) or the full path to the binary file of the application. 


---

### Post by kornelix on 2012-08-05
Are we talking past each-other? Or did I miss something?

The file type .RW2 is not listed at all, so how can I
choose an app or create a command for this file type?

Where is the knowledge kept about file types and associated
apps or commands?

---

### Post by ajgreeny on 2012-08-05
Install **ufraw** and **gimp-ufraw**, which will also mean installing gimp, of course, and you can then open those rw2 files in gimp with no problem.

---

### Post by OM55 on 2012-08-05
Sorry, stephen67 (first posting) was referring to an application that was already installed (gPHPedit) and supposedly had registered its mime type association. I assumed that this was the problem.
 
 However, if you need to add a new file type association here is how you do it:
 
 [U]The files you are looking for are placed in the following folders:
[/U] 
 System wide mime associations/extensions:
 **/usr/share/applications/defaults.list**

 Your own user specific mime associations/extensions:
 **~/.local/share/applications/mimeapps.list**
 
 All associations are by Mime types. Mime type file associations are set in groups (several file associations that are opened by the same application) and the information of which mime file associations and extensions is opened by a specific application is saved in the '.desktop' file, located at: **/usr/share/applications**
 The association list is in the MimeType line entry in the .desktop file.
 
 If you make any changes you should do them only in your local specific mime type association/extension list at: **~/.local/share/applications/mimeapps.list** because if there is any problem, you can easily copy it back to the original from another user and keep any other present or future user accounts clean.
 
 You typically will need to know the mime-type of the file you are adding, or just use 'other'. There are standard mime types for all known applications and information types, but if it is your own unique file extension (“MyApplication”) , you can register it as: application/MyApplication and create the .desktop file for it.

 You can find the .desktop file format specification at: [http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
 
You can also find more informaiton at the following link: 
[http://www.libre-software.net/change-the-default-application-ubuntu-linux](http://www.libre-software.net/change-the-default-application-ubuntu-linux)

 Hope that helps, or at least points you to the right direction this time!

---

### Post by kornelix on 2012-08-06
Thanks, but that is not what I wanted. I am still hoping someone knows the secret location of file types and their associated apps.

---

### Post by mcduck on 2012-08-06
> **kornelix said:**
> Thanks, but that is not what I wanted. I am still hoping someone knows the secret location of file types and their associated apps.

That is *exactly* what OM55 just posted... ;)

---

### Post by kornelix on 2012-08-06
OM55, thank you. 

I had tried doing some of what you suggest but it did not work - even after a reboot my additions were ignored. I will pay attention to the details you provided and try this again.

---

### Post by LewisTM on 2012-08-06
Here is a [guide]("http://ubuntugenius.wordpress.com/2009/11/19/create-your-own-file-types-in-ubuntu-with-assogiate/") on how to first create a **new** MIME type (e.g. Panasonic RAW) with **assogiate**, with links on how to subsequently specify what program to use for opening this file type.

Here's an [example]("http://ubuntuforums.org/showthread.php?p=11786078") of the creation of a new MIME type. Once this is done, Nautilus should detect it, give it a specific icon, and your can tell it to open it with GIMP or anything else you want.

Cheers!

---

### Post by ajgreeny on 2012-08-06
Perhaps 10.04 is different in this respect to 12.04, but never having used raw photo filetypes before and therefore having nothing that would open a photo I took to test this out, I simply made sure that ufraw and gimp-ufraw were installed, then right clicked on the rw2 file and used "Open with other application", chose gimp, and that automatically added rw2 files to the mime types listed in [B]~/.local/share/applications/mimeapps.list.

[/B]Nothing more was needed, so I am not sure why the OP is so worried about where the information is stored, or why he believes it is secret.

@OP  Have you installed gimp and the ufraw packages I mentioned and then opened a file with gimp yet?  It does work without a hitch, I promise.

---

### Post by kornelix on 2012-08-06
I got it working now. 
I added the following to ~/.local/share/applications/mimeapps.list

image/x-panasonic-raw2=gimp.desktop;
image/x-panasonic-raw2=kornelix-fotoxx.desktop;

Thanks for the help. Does anyone know why the simple method that worked in the past was removed? (the ability to associate an extension with a command (executable in /usr/bin).

---

### Post by OM55 on 2012-08-06
You are welcome. 
Now you can mark this thread as 'Solved' (not in the tag, but in the thread name).

---

### Post by kornelix on 2012-08-06
I don't see how to do this.
BTW I am not the originator of the thread.
I joined in when I saw it was my problem too.

---

### Post by cmcanulty on 2012-08-07
I also miss the option to browse for the correct app when it isn't in the list

---

### Post by ajgreeny on 2012-08-07
Oh my goodness!!

Having thought it was so easy, I have just booted into 12.04 (using the gnome-panel fallback DE) which I seldom use, opened nautilus and tried to do what I was telling others to do, and guess what?  It can't be done!

This is ridiculous, surely.  How are we supposed to open a file of unknown type with any application that is not in the list that appears;  where has the "Use custom command" option gone?  I know we can use a terminal to do it, but why not using nautilus as was possible in the past?

My apologies to the OP and others who may have thought I was being a bit rude, but it is the first time I have realised that this option no longer exists.

I presume this is all related to upstream gnome 3 changes, not ubuntu itself, but it is a heck of a loss, and something that I sincerely hope reappears in the fullness of time.

---

### Post by LewisTM on 2012-08-07
It can still be done with Thunar.
XFCE FTW.

---

### Post by cmcanulty on 2012-08-07
Oh thank you, how weird that I have to install Thunar to do a basic thing that was easy before!

---

### Post by ajgreeny on 2012-08-07
> **cmcanulty said:**
> Oh thank you, how weird that I have to install Thunar to do a basic thing that was easy before!
I agree!

nautilus in gnome 3, and therefore unity in 11.10 and 12.04 has lost several of the advantages that it had in gnome 2, and can no longer carry out things as was possible in the gnome 2 version.

Is this the "dumbing down" that many complain of?  If so, I think I will join them with a bit of a moan about it.

Simplicity is all very well until you can't do something that was possible, but has now been removed.  Progress?  I don't think so.

---

### Post by cmcanulty on 2012-08-08
yes I used to wait eagerly for the newest Ubuntu release and all the goodies it brought now I fear a new release for all that will be removed. Yet at the same time it uses more and more computer resources to do less.

---

### Post by LewisTM on 2012-08-08
GNOME is going down the path to "Linux for kindergarten kids", removing any sharp object or those one could swallow. 

I'm not the type to complain but rather find solutions. Xubuntu has been the one for me. While GNOME has gotten slower and less powerful, Xfce has become faster and more complete.

Cheers!

---

### Post by ajgreeny on 2012-08-08
> **LewisTM said:**
> GNOME is going down the path to "Linux for kindergarten kids", removing any sharp object or those one could swallow. 

I'm not the type to complain but rather find solutions. Xubuntu has been the one for me. While GNOME has gotten slower and less powerful, Xfce has become faster and more complete.

Cheers!
Agreed again!  So is Lubuntu, and even faster than Xubuntu, but perhaps slightly less easily configured, as text files need to be edited for some things to be changed.

However, all this gnome vs xfce vs lxde is discussed over and over on so many threads that it is getting boring.

And I confess I am one of those who keeps discussing the subject!

---

### Post by 3dart on 2013-02-08
check this  [http://ubuntugenius.wordpress.com/2009/11/19/create-your-own-file-types-in-ubuntu-with-assogiate/](http://ubuntugenius.wordpress.com/2009/11/19/create-your-own-file-types-in-ubuntu-with-assogiate/)

---

