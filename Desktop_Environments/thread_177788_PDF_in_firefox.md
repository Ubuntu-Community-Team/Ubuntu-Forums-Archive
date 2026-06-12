---
title: "PDF in firefox?"
date: 2006-05-16
forum: Desktop Environments
---

### Post by lemino on 2006-05-16
I don't get PDF to work very well in firefox... Earlier on, I associated gpdf as the default application to use for PDF-files. It then turned out to be a bad choice for some reasons. My problem now is that I don't seem to be able to change the association. If I have gpdf installed, it works, but if I uninstall it, firefox reports that the associated helperprogram is missing and that it for that reason can't display the file. There doesn't seem to be any pdf-entry in the settings either. I tried to do a full reinstall of firefox, but the problem remaines. HELP!

---

### Post by Sutekh on 2006-05-16
- I use **evince** over any other program.

You might like to look over these threads

[Ubuntu Forums - PDF viewers for Firefox?]("http://ubuntuforums.org/showthread.php?t=96061&highlight=evince")

[Ubuntu Forums - HOWTO: Embed PDFs with Evince in Mozilla/Firefox]("http://www.ubuntuforums.org/showthread.php?t=25685&highlight=firefox+pdf+viewer")
     


 - And of course there is the Acrobat Reader, **acroread**

[Ubuntu Packages - acroread]("http://packages.ubuntu.com/breezy/text/acroread")

Which can be installed from the multiverse repository and apt-get

 Do you know how to add repositories?  If so you need to enable the **multiverse** repository.  
 
 If you don't know how to add the multiverse repository, here's how.
 
 First you need to backup and edit the file that contains the repository sources.
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
 sudo gedit /etc/apt/sources.list
``` When the text editor opens you need to uncomment (remove the # sign) these lines
 ```
# deb http://archive.ubuntu.com/ubuntu breezy universe
 # deb-src http://archive.ubuntu.com/ubuntu breezy universe
 
 ...
 
 # deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` and add **multiverse** to the end of them.
 
 They should look like this
 ```
deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
  
 ...
 
 deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` Save the file and then refresh the repositories list and then install mplayer using these commands
 ```
sudo apt-get update
sudo apt-get install acroread
```

---

### Post by lemino on 2006-05-16
Thanks for the help!
I also prefer Evince since it's lightweight and does the job really well. (open source is also a big plus of course) I followed the guide for embedding Evince with mozplugger and it all worked out just fine. So, acrobat out, evince in! ;)

---

