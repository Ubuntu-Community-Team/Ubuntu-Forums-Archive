---
title: "Installing SecureFTP .bin file, add to menus"
date: 2006-01-05
forum: General Help
---

### Post by razumihin666 on 2006-01-05
In lieu of this ( [http://ubuntuforums.org/showthread.php?t=70963&](http://ubuntuforums.org/showthread.php?t=70963&) ) article, I am trying to install SecureFTP for access to my xbox.

I have managed to create a folder and extract the contents of the .bin file, but it's currently in my home/newdownloads/ folder.

My first problem, is that I don't know how to run the program. The second dilemna, is that I don't want it in my downloads folder. I'm not sure where I am supposed to install programs so they aren't cluttered in my downloads folder.
(Also, is there a way to add it to my 'Internet' menu. "Edit Menus" doesn't seem to have that option. And I'd rather not have to use a command line to run this program every time)

Thanks in advance.

---

### Post by quonsar on 2006-01-05
from the Glub Tech site, [http://www.glub.com/products/secureftp/docs.shtml]("http://www.glub.com/products/secureftp/docs.shtml")


> Unix

   1. If you don't have Java 2 (version 1.4 or greater), you must first download and install it.

   2. Download the latest version of Secure FTP.

   3. If you are running HPUX you will probably need GNU Tar to run the Secure FTP installer.

   4. The installer is an executable shell script. From a terminal, run the download as if it were an executable ( sh ./<installer>.bin ).

   5. Follow the installation wizard.

---

### Post by razumihin666 on 2006-01-05
[QUOTE=quonsar]from the Glub Tech site, [http://www.glub.com/products/secureftp/docs.shtml]("http://www.glub.com/products/secureftp/docs.shtml")[/QUOTE]

Yes, I have read the information on Glub Tech's URL. I have come this far. The place I am stuck at is where to install these files. It asks to define a directory, but I'm still new to Linux / Ubuntu. I don't understand the file heirarchy. I'd like t put the program in a place where it belongs, out of the way. In addition to that, I would like to have access to it in the Applications Menu bar, as if I installed it using the package manager.

:???:

---

### Post by gims on 2006-02-01
Hello, 

I'm new as well and I would like to know to which directory to install files...

But razumihin if you want to add it to the Internet menu then try this. Go to Aplications -> System Tools -> Application Menu Editor. In there Select Internet -> New Entry and type these

Name: SecureFTP
Comment: <blank>
Command: sudo secureftp (or something like that)
and select the run in terminal.

That should work

---

