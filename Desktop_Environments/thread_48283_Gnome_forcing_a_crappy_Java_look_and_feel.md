---
title: "Gnome forcing a crappy Java look and feel"
date: 2005-07-11
forum: Desktop Environments
---

### Post by Strife on 2005-07-11
So I am running a couple of Java applications, but when running it in Gnome, a crappy-looking excuse for an attempt to emulate Gtk is selected as the default look and feel for each app. However, since the default look and feel shows up in other environments (e.g., the default showed up when running fluxbox), I am fairly sure this is a Gnome issue.

I searched with gconf-editor, but there doesn't appear to be anything with the name 'java' in it anywhere.

Any idea what's forcing this and how I can unforce it?

---

### Post by jasmuz on 2005-07-11
[QUOTE=Strife]So I am running a couple of Java applications, but when running it in Gnome, a crappy-looking excuse for an attempt to emulate Gtk is selected as the default look and feel for each app. However, since the default look and feel shows up in other environments (e.g., the default showed up when running fluxbox), I am fairly sure this is a Gnome issue.

I searched with gconf-editor, but there doesn't appear to be anything with the name 'java' in it anywhere.

Any idea what's forcing this and how I can unforce it?[/QUOTE]
 What you are talking about is the older version of GTK, wich is rather ugly, but most programs that havent been exported yet to GTK2 rely on this. If it bothers you so much you could download and recompile the program and force it to use Gtk2.

---

### Post by gil-galad on 2005-07-11
No, what he is talking about is java programs attempting to look like gtk2 apps, and doing a poor job of it.  The themes that are supported actually work pretty well.  It doesn't really have anything to do with gnome, so there won't be any settings for it.  There might be some sort of java config.  

I don't really know what you can do about it.  Java apps are probably going to look ugly no matter what.

---

### Post by maruchan on 2005-07-12
Talk to the developers of whatever software it is you're using. It has come to the attention of the [Art of Illusion](http://aoi.sf.net) devs that the GTK look and feel is not going to work, so they're considering using (IIRC) jgoodies. I have no idea how it all works, but apparently jgoodies will only be used instead of the GTK laf, and not in other cases.

Good question, and the answer seems to be: Talk to your developers.

---

### Post by Strife on 2005-07-12
No, the answer is not really "talk to the developers" simply because the application does not select a look and feel. Therefore, if something is being forced to use one that is not the default one for Java (instead a default one set elsewhere), then something is wrong other than with the application itself.

---

### Post by SteveF on 2005-07-12
This comes from the Sun web site.  Maybe it will help you out:

Specifying the Look and Feel: Command Line

    You can specify the look and feel at the command line by using the -D flag to set the swing.defaultlaf property. For example:

java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel MyApp

java -Dswing.defaultlaf=com.sun.java.swing.plaf.windows.WindowsLookAndFeel MyApp

Specifying the Look and Feel: swing.properties

    Yet another way to specify the current look and feel is to use the swing.properties file to set the swing.defaultlaf property. This file is located in the lib directory of the Java release. For example, if you're using the Java interpreter in javaHomeDirectory\bin, then the swing.properties file (if it exists) is in javaHomeDirectory\lib. Here is an example of the contents of a swing.properties file:

# Swing properties

swing.defaultlaf=com.sun.java.swing.plaf.windows.WindowsLookAndFeel


How the UI Manager Chooses the Look and Feel

    Here are the look-and-feel determination steps that occur when the UI manager first initializes itself:

       1. If the program sets the look and feel before any components are created, the UI manager tries to create an instance of the specified look-and-feel class. If successful, all components use that look and feel.

       2. If the program hasn't successfully specified a look and feel, then the UI manager uses the look and feel specified by the swing.defaultlaf property. If the property is specified in both the swing.properties file and on the command line, the command-line definition takes precedence.

       3. If none of these steps has resulted in a valid look and feel, the program uses the Java look and feel. 

Steve

---

### Post by Strife on 2005-07-12
That may be helpful. I'll take a closer look at that later. I guess I should've checked Sun's site before automatically assuming a Gnome problem...

Thanks.

---

### Post by Strife on 2005-07-12
[QUOTE=Strife]That may be helpful. I'll take a closer look at that later. I guess I should've checked Sun's site before automatically assuming a Gnome problem...

Thanks.[/QUOTE]
 An update on this... I tried editing the swing.properties file to specify the default LAF, but this didn't work. Something, whether it be Gtk or Gnome, is still forcing it to use the damn crappy Gtk lookalike. I also couldn't get the command line way to get it to work, either.

Later on tonight, I'll whip up a test program and try that and see what happens.

---

### Post by Strife on 2005-07-12
So I really feel dumb.

I know I have seen this before with various applications, so that's why I thought that it was a Gnome-related issue.

However, browsing the source of this particular program I am running, it makes a call to ```
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
```

So, it really is this program. Thank goodness for open source software.

I also apologize for my idiocy.

---

### Post by maruchan on 2005-07-12
Apology accepted, Strife!  :razz:

---

### Post by Rounin on 2007-07-01
While I may be a couple of years too late, I think I know why you're still seeing the wrong look and feel as well. With applications that set the look-and-feel to the system LAF, the option to use is this:

java -Dswing.systemlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel

Obviously, you should replace the GTK LAF with whatever LAF you wish to use.

---

