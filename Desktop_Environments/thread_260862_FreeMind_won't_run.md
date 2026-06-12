---
title: "FreeMind won't run"
date: 2006-09-19
forum: Desktop Environments
---

### Post by xslf on 2006-09-19
I'm attempting to install & run Freemind.

I tried installing it using the instructions found in 
[http://blog.siliconchaos.net/articles/2006/05/22/setting-up-freemind-in-ubuntu-dapper](http://blog.siliconchaos.net/articles/2006/05/22/setting-up-freemind-in-ubuntu-dapper)
and (when that didn't work) running the self containing file from sourceforge.
In both cases, when I attempt to run freemind, I get the error:
```
sforbes@AMD:~/bin$ ./freemind.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at freemind.main.FreeMind.<init>(FreeMind.java:93)
   at freemind.main.FreeMind.main(FreeMind.java:647)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...6 more

```

Any clues? I have Sun's Java installed.

---

### Post by xslf on 2006-09-19
Replying to myself, in case someone else has the same problem:
I had to set my default Java to Sun's one, using the command
```
$ sudo update-alternatives --config java
```

---

### Post by pyros on 2006-10-27
yeah, I just uninstalled the java-gcj-compat package, and it did the same thing.

---

### Post by mogwai on 2006-11-03
I have successfully got this running on Edgy.

I used synaptic to grab 'sun-java5-bin' and 'sun-java5-jre'.
Then downloaded [freemind-bin-max-0_8_0.zip]("http://prdownloads.sourceforge.net/freemind/freemind-bin-max-0_8_0.zip?download")
Extracted it into a folder, right-clicked on the 'freemind.sh', selected 'Make link', then copied that link to my desktop and renamed it.

That was all I had to do.
Got the instructions from [here]("http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#On_any_UN.2AX_kind_of_system_.28also_Linux.29").

hth

mogwai

---

### Post by nyxynyx on 2007-01-02
How do you unzip the file? I got the following error:

Archive:  freemind-bin-max-0_8_0.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of freemind-bin-max-0_8_0.zip or
        freemind-bin-max-0_8_0.zip.zip, and cannot find freemind-bin-max-0_8_0.zip.ZIP, period.

---

