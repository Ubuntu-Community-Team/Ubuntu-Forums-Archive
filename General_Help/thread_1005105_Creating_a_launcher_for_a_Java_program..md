---
title: "Creating a launcher for a Java program."
date: 2008-12-07
forum: General Help
---

### Post by wonderbriefs on 2008-12-07
I  went through the long roundabout method of installing Webcamstudio, and would like to not always have to use the terminal to launch it.

I've installed it in home/webcamstudio
When I open the terminal and type the following command, it runs just fine.
```
java -jar ~/webcamstudio/WebcamStudio.jar
```

But when I right-click on the desktop, and try to create a launcher for an "Application in Terminal" the launcher doesn't work.

What's up?

---

### Post by kpkeerthi on 2008-12-07
If it is a GUI application, you could use **javaw** so you don't have to specify 'Application in Terminal' in the launcher. I'd use absolute path to the JAR, like so ```
javaw -jar /home/<user-id>/path/to/jar/app.jar
```

---

### Post by jamesstansell on 2008-12-07
> **kpkeerthi said:**
> If it is a GUI application, you could use **javaw** ...

ms/windows has a javaw command but I'm not aware that it exists for any other system.

---

### Post by jamesstansell on 2008-12-07
> **wonderbriefs said:**
> I  went through the long roundabout method of installing Webcamstudio, and would like to not always have to use the terminal to launch it.

I've installed it in home/webcamstudio
When I open the terminal and type the following command, it runs just fine.
```
java -jar ~/webcamstudio/WebcamStudio.jar
```

But when I right-click on the desktop, and try to create a launcher for an "Application in Terminal" the launcher doesn't work.

What's up?

Did you try the Application type of launcher?  Since it sounds like a GUI program it might not need the terminal launcher.

How does it fail?  Does it output any errors to the .xsession-errors file?

You might also ask the author, perhaps by posting to this thread:

[http://ubuntuforums.org/showthread.php?t=943774](http://ubuntuforums.org/showthread.php?t=943774)

---

