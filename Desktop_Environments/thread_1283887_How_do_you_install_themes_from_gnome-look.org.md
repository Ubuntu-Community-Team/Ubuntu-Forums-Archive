---
title: "How do you install themes from gnome-look.org?"
date: 2009-10-06
forum: Desktop Environments
---

### Post by COMTIBoy on 2009-10-06
I'm relatively new to Ubuntu Linux.

I noticed some really cool looking themes on gnome-look.org. 

Specifically, I really like this one: 

[http://gnome-look.org/content/show.php/chris0-OSX-Black?content=73945](http://gnome-look.org/content/show.php/chris0-OSX-Black?content=73945)

I can't figure out how to install these though and I can't seem to find any directions. See, I told you I was pretty green :) 

Anyhoo, I downloaded to my desktop and extracted the files so I'm left with this:

suaro@suaro-desktop:~/Desktop/Chris0-OSX-Black$ ls -l
total 24
drwxr-xr-x 19 suaro suaro 4096 2009-10-06 01:42 gtk-2.0
-rw-r--r--  1 suaro suaro  151 2008-01-20 16:51 License
drwxr-xr-x  2 suaro suaro 4096 2009-10-06 01:42 metacity-1
-rw-r--r--  1 suaro suaro  177 2008-01-19 20:35 panelbg.png
-rw-r--r--  1 suaro suaro  345 2008-01-20 16:59 README
drwxr-xr-x  2 suaro suaro 4096 2009-10-06 01:42 source


...but not sure how to go about installing it. 
The README file didn't have any installation instructions.

Thanks in advance for any tips. 
Regards

---

### Post by trstncmpbll on 2009-10-06
go to appearance themes and open em

---

### Post by COMTIBoy on 2009-10-06
That's what I originally tried. 
Went to Appearance \ Themes.  Considering that I don't know how to install the newly downloaded theme, I wouldn't expect them to (magically) be in the list of options.  I did select the 'Install' button from the Appearances Preference page and it provided me a navigation option. I pointed to the directory where I downloaded the files ( /home/suaro/Desktop/Chris0-OSX-Black )  but from there had no idea what to do.  I just pointed to the directory and nothing happened. It didn't seem to recognize any of the files :(

---

### Post by COMTIBoy on 2009-10-06
I just figured it out.

I clicked the 'Install' button from Appearance\Theme and pointed to the downloaded file :  73945-Chris0-OSX-Black.tar.gz file  .... rather than the directory to where I extracted it.  From there a prompt appeared that gave me the option to install.

Thanks!

---

### Post by pmlxuser on 2009-10-06
easy, extract them (say right click -> extract here). move folder to your home directory into a hidden folder .icons

ie say your extracted folder in home/username is blackicons then
```

$ mv blackicons ~/.icons

``` 
if folder does not exist, create it
```

$mkdir ~/.icons

```

Ohh sorry this is for just installing icons....

---

### Post by stinkeye on 2009-10-06
> **COMTIBoy said:**
> I just figured it out.

I clicked the 'Install' button from Appearance\Theme and pointed to the downloaded file :  73945-Chris0-OSX-Black.tar.gz file  .... rather than the directory to where I extracted it.  From there a prompt appeared that gave me the option to install.

Thanks!
You can also just drag and drop the tar.gz file in the Appearance Preferences window. Sometimes though, you have to extract the compressed theme you want first, because there may be other types of themes included in the archive.

---

### Post by COMTIBoy on 2009-10-06
Thanks for all the responses everyone!

Kind regards,

---

