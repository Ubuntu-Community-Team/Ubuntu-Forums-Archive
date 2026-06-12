---
title: "problem with eclipse"
date: 2005-10-14
forum: Desktop Environments
---

### Post by solstice on 2005-10-14
Hey all, i'm a noob. And it is way past my bedtime, figured i'd shout out for help before i pass out.

I have been using eclipse for quite some time on lots of platforms, including hoary kubuntu. Today i just installed ubuntu and am having trouble setting up eclipse.

I have tried multiple versoins of eclipse, 3.0, 3.1, 3.1.1 and they all error in different place. for example, if i try running the 3.1 version, eclipse will load but I get this error:

"Unable to create this part due to an internal error. Reason for the failure: The editor class could not be instantiated. This usually indicates that the editor's class name was mistyped in plugin.xml."

specifically: java.lang.ClassNotFoundException: org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitEditor

I believe I have set up my paths correctly, I can type java and javac (anywhere) and  run them...

The other versions of eclipse get the same type of problem in different places. One I got to bring up source files but it won't do syntax highlighting.

Like I said, I'm still a linux noob. any help would be very appreciated! Thanks!

---

### Post by solstice on 2005-10-14
anyone have this problem? anyone successfully get eclipse to work?:confused:

---

### Post by ichiban on 2005-10-14
How did you install Eclipse ? 

Did you use Add Applications ?

---

### Post by chadwick359 on 2005-10-14
I do have Eclipse working, but I admit, I haven't seen that error. I would suggest using synaptic, or 'sudo apt-get install eclipse-common eclipse-ecj' those will install all of the dependencies, and Eclipse should work from there on out.

---

### Post by solstice on 2005-10-14
no, I extracted the gzip archive, put it where i wanted it, and double clicked the executable. I thought this would have configured itself as it always has in the past.

I'm at work now so i can't try the add application button for awhile, could this fix the issue?

---

### Post by riggsd on 2005-10-14
It's probably gij trumping Sun's Java as default. Type 'java' at the command line to see which version is default.

Switch to Sun's JDK by either:

```
$> sudo update-alternatives --config java
```

or

```
$> apt-get remove --purge java-gcj-compat
```

---

### Post by chadwick359 on 2005-10-14
Yeah, the archive version will try to predict where java is installed, but doesn't always get it quite right. Installing from synaptic is almost always more stable and right now, the synaptic package is already 3.1.1, so you will be up to date.

---

### Post by solstice on 2005-10-14
i did a search in synaptic for eclipse and the only thing i saw was a 3.0 bootstrap version...what was this? 

I did try the update default last night but no the remove command.

How do i get the 3.1.1 version through synaptic?

Thanks a lot for all of your help:D  Much appreciated!

---

### Post by solstice on 2005-10-14
one last bump for my last questions above. (I want to have a game plan for when i finally get home.)

---

### Post by galderz on 2005-12-20
i'm having problems installing eclipse 3.1.1 as well. I keep getting "unable to read workbench state" and the main eclipse screen contains nothing. It's only the eclipse framework that shows, nothing else. Anyone had similar problem?

---

### Post by elemental666 on 2005-12-20
enable all your repositories, its either in multi or uni, don't remember which.

I get eclipse running fine, but am having a hell of a time getting phpEclipse to install correctly.  I unzipped the phpEclipe 1.4 features into the /usr/lib/eclipse/ dir and restarted eclipse.  I see the new stuff when I got to Help->Manage config (or whatever) but when I try to enable them I get errors about no such files or directories...

So I decided to completely remove it, which to my dismay didn't work. Synaptic and apt think its gone but there are tons of files left on my system...

---

### Post by elemental666 on 2005-12-20
double post, sorry...

---

