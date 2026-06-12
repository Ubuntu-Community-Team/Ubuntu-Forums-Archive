---
title: "How can I make this executable?"
date: 2010-05-10
forum: Gaming &amp; Leisure
---

### Post by sanderella on 2010-05-10
After I did my upgrade I can't get wordbiz to load. It is the internet scrabble site. Can anyone tell me how to fix this? I don't understand the explanation.:(

The file '/home/sandra/.cache/.fr-bZKFtW/WordBiz/wordbiz.jar' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Kevinator on 2010-05-10
I'm not sure, but I don't think a .jar file should be executable. It's not a script or native binary, it's a Java package. Can you explain what you are doing that produces the error message? Is this supposed to be a web page applet or a downloaded application? Edit: And if it's an applet, do you have the Java plugin installed?

---

### Post by AdotB on 2010-05-10
Make sure you have java installed and try running it with this:
```
java -jar wordbiz.jar
```
If that works, you can try adding `java -jar' under `open with' in the properties for that file.

---

### Post by themusicalduck on 2010-05-10
When it says it isn't marked as executable it means that it doesn't have permission to run, a security feature in Ubuntu. To change this you find the file (/home/sandra/.cache/.fr-bZKFtW/WordBiz/, hit ctrl+h to show files with a . before them), right click on it, click Properties, Permissions tab and check the box next to Allow executing file as program.

Or you could use ```
sudo chmod +x /home/sandra/.cache/.fr-bZKFtW/WordBiz/wordbiz.jar
``` in a terminal (or with whatever the fie location is).

But since this is a temporary file from a website I'm not sure how well it will work.. if you refresh the page it might just download a new file without the right permission again. It's worth a try using those methods though.

---

### Post by hikaricore on 2010-05-10
You don't need to use sudo to chmod a file in your home directory..  :rolleyes:

---

### Post by themusicalduck on 2010-05-11
> **hikaricore said:**
> You don't need to use sudo to chmod a file in your home directory..  :rolleyes:

Oh good point :P I sometimes just automatically put a sudo in front of that command without thinking about it!

---

### Post by ELD on 2010-05-11
> **themusicalduck said:**
> Oh good point :P I sometimes just automatically put a sudo in front of that command without thinking about it!

Just to point this out, that is a really bad habit to get into, you could fry your system with one overlooked command that way mate.

---

### Post by sanderella on 2010-05-12
Thanks for all your help. I can get into the backup server now and play with the computers. Time and patience will get me into the main play area.:)

---

### Post by sanderella on 2010-05-17
I found out how to do this. Right click on the icon > properties > permissions > enable all accesses and tick 'execute'. Wordbiz now is executable.

:popcorn:    :popcorn:    :popcorn:    :popcorn:

---

### Post by ELD on 2010-05-17
> **sanderella said:**
> I found out how to do this. Right click on the icon > properties > permissions > enable all accesses and tick 'execute'. Wordbiz now is executable.

:popcorn:    :popcorn:    :popcorn:    :popcorn:

Exactly the same as @[themusicalduck]("http://ubuntuforums.org/member.php?u=565084") posted but yours is using the UI.

---

### Post by mecanopsis on 2010-10-27
Using XUbuntu 10.10, I don't have the option referred to above (icon > properties > permissions) to make wordbiz executable, no doubt I need to download something from somewhere to make this possible. Any ideas, please ?

---

### Post by mecanopsis on 2010-10-27
From posts elsewhere on this site, it seems there is a real problem with executable files on 10.10

---

