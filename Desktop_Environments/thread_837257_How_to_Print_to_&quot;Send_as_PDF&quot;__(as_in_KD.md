---
title: "How to Print to &quot;Send as PDF&quot;  (as in KDE or OpenOffice)"
date: 2008-06-22
forum: Desktop Environments
---

### Post by mexlinux on 2008-06-22
Hi:
Is it possible to create a pseudo printer to print as PDF and have that piped to an email in evolution?

Just as the beahavior of kprinter in KDE for printer "Send as PDF)
or OpenOffice.org wich even have this option in the menu.

Thanks

---

### Post by mexlinux on 2008-07-08
OK, since this is something I really need I came with a quick and dirty solution, that works very good for me.

When you print to the PDF printer
It provides a Save As dialog (so you can save to your prefered location, not just to /home/user/PDF ) that also include a "Don't Save, Email the PDF" button (see the attached screenshot).

This is how I accomplished:
1-Download the attached postpdf.xml.txt and save to your preferred location, and remove the .txt at the end of the name to make it be just "postpdf.xml".

2-Download the attached postpdf.py file (save to the same folder as the above file)and modify the line 42 to math the path to your file, example:
```
builder.add_from_file("/path/to/your/file/postpdf.xml") 
```

3-Download the attached postpdf.sh.txt and save it to your preferred location, remove the .txt at the end of the name to name it just "postpdf.sh"
And modify the last line to match the path to your file, example:
```
/path/to/your/file/postpdf.py "${CURRENT_PDF}"
```

4-As root, edit the file (make back up every time you modify a system file) /etc/cups/cups-pdf.conf
Almost at the end you will find the Key Postprocessing, add the following line (modify the path, of course):
```
PostProcessing /path/to/your/file/postpdf.sh
```

5-As root, edit the file (make back up every time you modify a system file) /etc/apparmor.d/usr.sbin.cupsd at the end (but before the closing bracket "}") add the following line (modify for your path):
```
  /path/to/your/file/postpdf.sh uxr,
```

6-Restart apparmor with the following command:
```
sudo /etc/init.d/apparmor restart
```

That's it, hope it helps someone.

PS: I'm also attaching the postpdf.glade file in case you want to modify it.

---

### Post by mexlinux on 2008-07-08
I have added this as an idea in brainstom:
[http://brainstorm.ubuntu.com/idea/10900/]("http://brainstorm.ubuntu.com/idea/10900/")

---

### Post by paulo21 on 2008-08-21
mexlinux,
Could you help me? I did as you told, but It didn't work. Why's that?

Thanks in advance.

---

### Post by mexlinux on 2008-08-23
paulo21
I didn't wrote it before, but you have to give executable permission to the .py and .sh files... did you geve it?

---

### Post by pohl9876 on 2008-08-31
Hi,

I followed the tutorial in this thread and get the following error messages when running "postpdf.py file.pdf" directly on the command line:

Traceback (most recent call last):
  File "/etc/cups/postpdf.py", line 52, in ?
    mipost = PostPdf()
  File "/etc/cups/postpdf.py", line 37, in __init__
    builder = gtk.Builder()
AttributeError: 'module' object has no attribute 'Builder'

Which python packages have to be installed to make the script work (other than python-gtk2 and python-glade2)? Does anybody know what the problem for those messages is? I have no experience in python and don't know where to start looking.

Alexander

---

### Post by mexlinux on 2008-08-31
sound like It needs a newer GTK that supports GtkBuilder. 
Which version do you have?

---

### Post by maddentim on 2009-03-18
I don't think this worked for me.  I followed the guide, but got this error message when I restarted apparmor

```
user@ubuntu:/etc$ sudo /etc/init.d/apparmor restart
Reloading AppArmor profiles Warning (/etc/apparmor.d/usr.sbin.cupsd line 1118): Unconfined exec qualifier (ux) allows some dangerous environment variables to be passed to the unconfined process; 'man 5 apparmor.d' for details.
 Skipping profile /etc/apparmor.d/usr.sbin.cupsd~
: Warning.

```

Seems like a good solution, so if anyone has a fix for me let me know.

---

### Post by BigBopper on 2009-04-01
> **mexlinux said:**
> OK, since this is something I really need I came with a quick and dirty solution, that works very good for me.

When you print to the PDF printer
It provides a Save As dialog (so you can save to your prefered location, not just to /home/user/PDF ) that also include a "Don't Save, Email the PDF" button (see the attached screenshot).

This is how I accomplished:....

Nice howto.  However, I prefer KDE.  I have used your instructions but get an error about DCOPServer.  I'm sure it's just a permission thing on the desktop, but I have no ideas on how to fix it.  Any help would be appreciated.

Al

---

### Post by mexlinux on 2009-04-11
@maddentim that from apparmor is not an error is just a warning because as it says "allows some dangerous environment variables to be passed to the unconfined process", wich is exactly what we want in this case...

---

