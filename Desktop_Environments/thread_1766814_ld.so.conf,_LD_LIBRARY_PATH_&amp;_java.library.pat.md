---
title: "ld.so.conf, LD_LIBRARY_PATH &amp; java.library.path"
date: 2011-05-24
forum: Desktop Environments
---

### Post by areeda on 2011-05-24
I'm working with 11.04 but this issue has been around for a while.

If the title made sense to you, you probably already understand but here's the problem.

I use NetBeans for development but any Java application that is started by the launcher has this problem.

Java searches for external dynamic libraries based on java.library.path which is set when the JVM starts from LD_LIBRARY_PATH.  But Ubuntu doesn't let us set LD_LIBRARY_PATH anywhere except in the user's .profile (or .cshrc..) so it's not available to anything run from the application launcher.

Java doesn't use ld.so.conf and bash doesn't allow dots (.) in environment variable names.

There must be a way to affect LD_LIBRARY_PATH or java.library.path for programs started by the launch but I can't find it.

Has anyone solved this?

Joe

---

### Post by Petr Kopac on 2011-11-12
Hi! I've got an older Ubuntu, but the problem is the same. On another forum I saw your question as well and you mentioned you used Xuggler - guess what, me too.

This is a system-wide bug (or a feature, depends on your POV), but definitely ubuntu doesn't behave in a standard way, unfortunately.

I solved it by an acceptable workaround - made a properties file with a key with the path, which I load at startup of my app. So if the user needs to change it, it's easy. In main() I have the attached code. I don't know how much general this issue is, but in Windows the library worked :/ Maybe you should file a bug?



```

    private final static String SETTINGS_FILE = "settings.properties";
    private final static String XUGGLE_KEY = "xuggle.lib.path";
    private final static String LD_LIBRARY_PATH = "java.library.path";

...

String libPath = settings.getProperty(XUGGLE_KEY);
if (libPath != null) {
  System.setProperty(LD_LIBRARY_PATH,  System.getProperty(LD_LIBRARY_PATH) + ":" + libPath);
}

```

**EDIT**

Just after I posted this I stumbled upon even worse issue with this library. It's got its own versions of various libraries, which are used in the system as well. So even when you managed to apply the configuration system-wide, audio-video programs would stop working, because they would crash. I found it when I ran mplayer yesterday in BASH with LD_LIBRARY_PATH changed - ldconfig just uses the latest version of the library it can find. So when I add /usr/local/xuggler/lib, it uses it for all programs.

So I had to change the netbeans launcher to first export LD_LIBRARY_PATH=/usr/local/xuggler/lib/ and then launch netbeans. For deployment, the application will have to be run through a simple script. So this whole concept of system-wide installation of Xuggler is actually not viable.

I think I'll just take all the files for Windows and Linux and put them into a package with my app and create two launchers respectively.

I'm wondering, whether I'll have to solve more problems before actually programming, the deadline is near ](*,)

---

