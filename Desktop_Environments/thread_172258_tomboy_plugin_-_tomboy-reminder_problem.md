---
title: "tomboy plugin - tomboy-reminder problem"
date: 2006-05-08
forum: Desktop Environments
---

### Post by matej on 2006-05-08
Hello,

I found very usefull tomboy plugin for reminding notes. See [http://raphael.slinckx.net/tomboy.php]("http://raphael.slinckx.net/tomboy.php")  But I have problems with geting it work:[LIST]
[*]ubuntu or debian package is probably not available
[*]precompiled version crashes tomboy (on breezy - tomboy 0.3.2-9ubuntu4; dbus 0.36.2-0ubuntu7)
[*]compilation failed[/LIST]```
Making all in src
make[1]: Entering directory `/home/x/Desktop/tomboy-reminder-0.9/src'
mcs -debug -out:tomboy-reminder.dll -target:library -pkg:tomboy-plugins Reminder.cs MagicTime.cs MagicDate.cs MagicParser.cs MagicUtils.cs
Reminder.cs(59) error CS0117: `Tomboy.Note' does not contain a definition for `TagTable'
Reminder.cs(63) error CS0117: `Tomboy.Note' does not contain a definition for `TagTable'
Compilation failed: 2 error(s), 0 warnings

``` 
Any clue?

---

### Post by Sef on 2006-05-08
> Download
Requirements

The latest version of the plugin requires:

    * tomboy-0.3.2 or higher
    * dbus-0.23.4 or higher if tomboy is compiled with dbus support (previous version make tomboy crash when using plugins)(note that this plugin doesn't use dbus)



How did you install it?  From the repositories or from their site?  What version do you have?

---

### Post by matej on 2006-05-08
[quote=Sef]How did you install it?  From the repositories or from their site?  What version do you have?[/quote] 
I cannot find packages, so I used for first precompiled version and after it failed, I tried to compile that from sources. I used last version - 0.9.

---

