---
title: "Opening .PL files In Firefox"
date: 2009-01-23
forum: General Help
---

### Post by crokett on 2009-01-23
I hope this is an easy one.

My company has a website for standard programs we can download and install.  The problem is the automated installer is a perl script. Firefox for Windows handles this with the OSPFile helper. Firefox for Linux doesn't know what the .pl file is and wants to use a text editor to open it.  How can I tell Firefox the proper way to handle the file?  I checked about:config on Windows Firefox but didn't see anything in there about handling these files.  I also googles OSPFile and Linux but didn't find anything.

---

### Post by pennacook on 2009-01-23
I believe you will need to add the mime type on the web server itself in /etc/mime.types

application/x-perl	pl

---

### Post by ibuclaw on 2009-01-23
This is because all files you download from the internet onto Linux loose all their execute permissions (Security, Security, Security! :)).
You're better off saving the file, running '**chmod +x foo.pl**' and executing it that way.

Regards
Iain

---

### Post by binbash on 2009-01-23
you cant execute it.End of story.It is not about mime types etc.

---

### Post by ProgramErgoSum on 2009-01-25
You need to do the "First time" setup. :wink: :wink:

---

### Post by crokett on 2009-02-06
> **ProgramErgoSum said:**
> You need to do the "First time" setup. :wink: :wink:


Forgot I posted this thread.  It is fixed. Thanks.

---

### Post by parselva on 2009-02-20
I am also facing this problem. I couldn't find a solution for this...
Could you please help me on this?

---

### Post by ilmw on 2009-04-09
> **crokett said:**
> Forgot I posted this thread.  It is fixed. Thanks.

Hi crokett

How did you fix it? I have the same problem now. Thanks!!

---

### Post by vamped on 2009-11-06
This seems to be an ongoing problem dating back to ~2005. 30 minutes of searching and all I came up with was an add-on the didn't really do the trick for me, "Open in Browser" (it prompts every time i want to open a file). Then I figured out a solution.

Easy Soution:
create file ~/.mime.types

Add the following line and put whatever file extensions you want, ie (pl py):
text/plain pl py

This tells the browser to treat these file types as plain text. 

Using Firefox 3.5.4

---

