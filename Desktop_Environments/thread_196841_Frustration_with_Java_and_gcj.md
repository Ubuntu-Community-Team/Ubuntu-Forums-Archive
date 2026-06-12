---
title: "Frustration with Java and gcj"
date: 2006-06-14
forum: Desktop Environments
---

### Post by korny on 2006-06-14
Hi all,

I'm a Java developer, relatively new to Ubuntu, and I am finding the Ubuntu java packaging a complete nightmare.  I'm mainly writing here out of frustration; though if others can point out an easy way to configure Java tools without doing all the work myself, I'd be a happy man :)

The basic problem is that while Ubuntu allows you to install Sun's Java, it defaults to gcj all over the place, and there is no easy way to change this.  Surely if someone has chosen to install Sun's Java, Ubuntu could accept that decision and actually use it?

I understand the politics behind gcj, and I support the fact that it is the default java environment - the default option should be the completely free one.  However, gcj is still severely limited in several areas - not least, the fact that it doesn't support Java 1.5 language features.  This makes it not very useful, for me at least, in my day-to-day work.

However, in Dapper I can't get rid of the damn thing.  Every java tool has gcj as a prerequisite, as well as a pile of other related libraries.  Surely there is some way in apt for the system to recognise that I *have* a working JVM, and don't need to download all this extra stuff?

Worse, despite using the update-alternatives and update-java-alternatives mechanisms, many tools still use gcj.  Eclipse is a case in point - as bundled with Ubuntu, it completely ignores the update-alternatives symlinks and uses gcj, unless you manually edit a config file.  This may be ok if you are only doing gcj development, and not using a single tool or plugin that relies on Java 1.5 features - but it's not much use for the rest of us.

Ditto anything that looks for JAVA_HOME to identify a JVM - update-alternatives doesn't set JAVA_HOME, so such tools are also out of luck.  Sigh.  Suse used to have this working much more easily - it had a script to set JAVA_HOME and related environment variables on the fly, and then "/usr/bin/java" and related tools were scripts that interrogated JAVA_HOME and chose the right JVM for the current shell.  Changing JVM could be done on a per-script basis.  It looks like Suse 10 has moved to the update-alternatives mechanism however.  Pity the person who wants to run two different JVMs at once...

In the end, I've given up on apt for my Java tools. I use it to install and update Java itself, and I use java-package to install other things like beta versions of Java 1.6, but I'm installing everything else by hand.  That way I know they work, and won't be mysteriously running gjc behind the scenes, and I can tweak their startup scripts to run the right JVM, without worrying about collisions with automatic updates.

I know the real culprit is probably Sun, with their annoying restrictions on Java packaging - if they open-sourced Java, half the problem would go away.  But given the fact that Ubuntu now allow you to install Sun's java, it'd be nice if it actually worked. :-/

- Korny

---

### Post by Nequeo on 2006-06-14
[edit] never mind... didn't read your entire post [/edit]

---

### Post by vinodis on 2006-06-15
where does it revert to gcj mysteriously?
I've set the env_vars in the /etc/environment and no issues as such.

---

### Post by mattkenn4545 on 2006-06-15
sudo update-alternatives --config java

---

### Post by mattkenn4545 on 2006-06-15
recommend doing 

sudo update-alternatives --all

to check every alternative

---

### Post by korny on 2006-06-15
[QUOTE=vinodis]where does it revert to gcj mysteriously?
I've set the env_vars in the /etc/environment and no issues as such.[/QUOTE]

I didn't mean to say that it reverts mysteriously - but several programs when you install them have gcj as prerequisites, which forces you to install gcj; and then they use gcj even if you have update-alternatives set to Sun's java.  Eclipse is a primary example of this - as installed by Ubuntu, it picks the first jvm it can find in the file /etc/eclipse/java_home.

And yes, you can manually set JAVA_HOME etc. in /etc/environment - but it doesn't keep in sync with update-alternatives, and comes under the category of "guru knowledge" in my opinion - I'd never even heard of this file :)  Also only *some* tools use JAVA_HOME.

A summary of what I've observed so far:
- You can set your JVM in (at least) 3 ways:
  (A) - running "update-alternatives" or "update-java-alternatives", which set symlinks from /usr/bin/java* -> /etc/alternatives/java* -> /usr/lib/j2sdk...etc

  (B) - setting JAVA_HOME, JRE_HOME, JDK_HOME etc to the correct paths, either in /etc/environment or in a shell script or .bashrc or the like.

  (C) - modifying /etc/eclipse/java_home and/or /etc/jvm (or other obscure config files)

- Java tools in the ubuntu repositories tend to use some combination of (A) (i.e. look for java on the path) or (C) (i.e. read an obscure config file).  Those that use (A) obey update-alternatives settings, those that use (C) don't.

- Java tools you install yourself tend to use (A) or (B) or both - i.e. Tomcat uses JAVA_HOME if it's set, otherwise it looks for java on the path.  This seems to be fairly standard behaviour.  (A) works with update-alternatives, (B) doesn't.

None of these options allow you to choose a JVM in Ubuntu without knowing which magic config files to edit, or which command-line tools to run.

And there are about 1000 howtos on the net about *which* config files and/or command line tools you should run - most of them wrong, or at least incomplete.

- Korny

---

### Post by korny on 2006-06-15
[QUOTE=mattkenn4545]recommend doing 

sudo update-alternatives --all

to check every alternative[/QUOTE]

Take a look at update-java-alternatives - it's basically a wrapper around update-alternatives that runs it for all java binaries.

Mind you, as per my previous rant it only works for some programs.

---

### Post by pecanov on 2006-06-15
You claim to be a Java developer, and yet it seems you haven't set up java before (no hard feelings).

If you don't want to update alternatives, or have problem with it, set JAVA_HOME in your bashrc or the global one, and prepend it at the same place to the PATH variable.

---

### Post by korny on 2006-06-16
[QUOTE=pecanov]You claim to be a Java developer, and yet it seems you haven't set up java before (no hard feelings).

If you don't want to update alternatives, or have problem with it, set JAVA_HOME in your bashrc or the global one, and prepend it at the same place to the PATH variable.[/QUOTE]

You misunderstand - I've set up java many many times on a wide range of platforms - but given it is now in a fairly mainstream apt package, I'd quite like it to be a seamless integration, so Java applications "just work" without needing manual tweaking.

Sure, *I* can get it working, but I'm not so certain about the vast body of new users who don't have a high level of experience with all this mess - they will have to rely on gleaning information from the long list of incorrect HOWTOs out there, or reverse-engineering shell scripts, or luck.

- Korny

---

### Post by beameup on 2006-06-17
While using the Dapper flight series I installed Sun Java by following the instructions in the Wiki to create a deb package from the downloadable bin file. To install the updated version in Add/Remove will I have to uninstall the other first?

I went ahead and installed it. And this is what my java config looks like. Which one do I select? #1 or #4. 
> There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2re1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java
      4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

Korny is right, It's not for the average Joe. 

I use Moneydance financial software which requires Java. I had to use the installer with Java. It placed JRE1.5.04 in the Moneydance install folder. It doesn't see the newer java version. I'll inquire about that with them.

---

### Post by beameup on 2006-06-18
[BUMP]   Dang! :?:

---

### Post by HippoMan on 2006-06-23
I have concerns that are somewhat similar to korny's.  Here's what I want on my system:

1. Sun's latest 1.5.x jdk

2. No instance of gcj on my system ... not anywhere!

3. Eclipse, using Sun's jdk.

I know how to accomplish number 1:  I downloaded Sun's latest jdk and ran **make-jpkg** in the appropriate manner.  Then, I installed the resulting package with dpkg, and everything worked fine.  Invoking **javac -version** shows that I am indeed running Sun's java.

However, achieving number 3 along with number 2 is problematic.  I can easily uninstall gcj and its dependencies, but if I then use aptitude to attempt to download eclipse, gcj and number of packages which use it get included in the list of downloads.  If I delete these from that list, I get unsatisfied package references.

Yes, I know that I can use the apt system to install eclipse anyway, and then I can change /etc/environment and possibly other configuration files in order to ensure that eclipse uses Sun's java.  But that doesn't satisfy requirement number 2, as gcj is back on my system.

The only solution I have been able to come up with is to download the eclipse tarball from the eclipse web site and install it directly from this tarball. Eclipse then uses the Sun  jdk and all works well, but the price I pay is that I don't have a "pure" system any more (from a debian/ubuntu packaging point of view).

If this is the only way that I can satisfy my three requirements, then so be it.

But hope springs eternal, and therefore, I humbly ask if any of you can think of a way for me to somehow install eclipse via the debian packaging system and still meet the requirements that I outlined above?  Since the eclipse download consists simply of unpacking a tarball into the desired location, is there perhaps a debian or ubuntu utility which will build a bona fide .deb file from such a tarball, in much the same  way that make-jpkg can do that with Sun's jdk installer?

Thanks in advance.

---

### Post by hanasaki on 2006-06-24
sun 1.5.x is now in the repositories...
dont worry about if something else put in gnu java.. just make sure the default alternative is the sun one

might want to take alook at [www.netbeans.org](www.netbeans.org) from Sun... I use both that and eclipse and they are both free.

---

### Post by HippoMan on 2006-06-24
Thanks.  In a little while I'll check out sun 1.5.x in the repositories.

And yes, I agree that Netbeans is also very good.

Maybe I'll bite the bullet and allow gcj to be installed, after all.  I've just come across anecdotal information that seems to indicate that some of the debian or ubuntu software that uses java will bypass the alternatives system and make use of gcj, whether I like it or not.

Or is that just an urban legend?

---

### Post by hanasaki on 2006-06-24
Post the link and give it a try.  Let's see the results.

---

### Post by HippoMan on 2006-06-24
Actually, it turns out to be in this very thread.   Here's the link to the first post: [http://ubuntuforums.org/showthread.php?t=196841]("http://ubuntuforums.org/showthread.php?t=196841")

Look at the paragraph which starts with the words "Worse, despite using the update-alternatives and update-java-alternatives mechanisms ...".  Perhaps this only pertains to eclipse, and maybe the update{-java,}-alternatives mechanism works for each and every ubuntu app that needs java, after all. 

I vaguely remember seeing a similar point being raised elsewhere, but I don't recall where.

But if these concerns are not founded, then great.

---

### Post by hanasaki on 2006-06-24
I set the following in /etc/profile
JAVA_HOME=/usr

You can even shoehorn in Mustang 1.6 but lets leave that for a later date after you get mainstream stuff working.

OK... so let's go back to problem solving / debugging 101 :cool:

What is the current state of the system?
What is the desired state?
What did you attempt and what were the results?  
Don't answer "it doesnt work"  that is a conclusion.  What is happening that leads you to the conclusion it doesnt work?  What do you see? Msg's? What do you observe?

Give me a cookbook recipe to recreate what you have.  Hmm does this belong in this thread? Or has HippoMan hijacked Kory's thread and should perhaps start a new thread?  Just checking...

---

### Post by HippoMan on 2006-06-24
Just keep in mind that I have not found ANY errors.  I have nothing to debug, and in fact, debugging is totally irrelevant to the points I've made and to the questions that I am asking.  I'm simply talking about experiences and successes with java and eclipse, and about concerns that other people have raised, especially korny, the person who started this current thread, and I am wondering about the validity of these concerns.

Feel free to move my comments, questions, and concerns to another thread if it's confusing or inappropriate to discuss them here in korny's thread.

---

### Post by anarhistu on 2006-06-26
Ok, Regarding Eclipse:

[http://ubuntuforums.org/showthread.php?t=201378&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=201378&highlight=eclipse)

Basically, the idea is:

Eclipse uses the JAVA_HOME visrtual machine by default, or if you do not have that, eclipse gets whatever it finds first in /etc/eclipse/java_home

This is mine, it goes with sun jdk 1.5.0.06

> cat /etc/eclipse/java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#add the sun java vm first
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06
#and then the rest if it goes wroong
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun


---

### Post by Bear Knuckle on 2006-06-28
I found this thread, because I was also very annoyed of the fact, that eclipse uses gjc instead of the sun-jre.
I finally managed to get eclipse to work with sun by doing, what anarhistu also suggested. But I prefer the following:
```

#This uses the symlink, which stays the same even on an update of the sun-jre
/usr/lib/jvm/java-1.5.0-sun
#and the rest, which at least I don't want to use in eclipse.
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads

```

Why I am writing here? Because I saw quite a bit of strange thing. Using gjc eclipse shows me a memory usage of "64M of 75M", but with suns-1.5-jre it's "10M of 14M".


Now tell me it's no good idea to use suns-jre?

---

### Post by korny on 2006-06-28
I'm fairly sure this is because Sun's java is showing the memory *currently* allocated, not the total memory available - so you have 14M of memory allocated, but if you hit this limit Java will allocate more memory.

I'm not running the apt-installed eclipse, so I can't tell what parameters it uses, but if I run the standard eclipse installer, and then run "jps -v" in another window to see startup parameters, I see:
    startup.jar -Xms40m -Xmx256m
So the default eclipse allocates a minimum of 40m, and a maximum of 256m.
(I don't have the memory usage panel visible within eclipse, by the way - I can't remember how to enable this!)

I assume gcj is allocating memory differently, so showing memory use differently.

You might try "jps -v" on your system to see what the apt-installed eclipse runs - or read through the startup scripts.  But I doubt it's a problem.  (Note jps only works with Java 5 or later)

---

### Post by hod139 on 2006-06-28
[quote=korny]

Worse, despite using the update-alternatives and update-java-alternatives mechanisms, many tools still use gcj.  Eclipse is a case in point - as bundled with Ubuntu, it completely ignores the update-alternatives symlinks and uses gcj, unless you manually edit a config file.  This may be ok if you are only doing gcj development, and not using a single tool or plugin that relies on Java 1.5 features - but it's not much use for the rest of us.

Ditto anything that looks for JAVA_HOME to identify a JVM - update-alternatives doesn't set JAVA_HOME, so such tools are also out of luck. [/quote]

For eclipse this is a [known bug.]("https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/45347") I can't speak for other java packages though.  I agree the ubuntu maintainers are not doing a great job at having all java application use the java-common scripts.  If ubuntu wishes people to use the update-alternatives mechanism and the java-common tools, then they should make all the packages respect them.

Aside: It warms my heart to see my howto linked in another thread :)

---

### Post by korny on 2006-06-28
[QUOTE=hod139]For eclipse this is a [known bug.]("https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/45347") [/QUOTE]

goodness - this bug links to yet another config script I've never seen before - /usr/share/java-common/jvm-find.sh - which seems to scan the following files for jvms:
$HOME/.jvm.d/$1
$HOME/.jvm
/etc/jvm.d/$1
/etc/jvm

So it seems that they intend to have a scheme for at least having a user-level override of jvm selection.  Though this script is not currently set as executable, so I'd guess it's still somewhat theoretical.

I really wonder how users are meant to find this stuff - if there is any documentation, it's invisible to me, and google-searching for "jvm-find.sh" and "java-common.sh" doesn't help much.

For now, I'm sticking to using update-java-alternatives to put my "preferred" jvm into the path, setting JAVA_HOME manually, and ignoring the ubuntu apt sources for everything else java related.  It just seems easier - everything outside of Ubuntu respects either the path, or JAVA_HOME.

---

### Post by hod139 on 2006-06-28
[quote=korny]
For now, I'm sticking to using update-java-alternatives to put my "preferred" jvm into the path, setting JAVA_HOME manually, and ignoring the ubuntu apt sources for everything else java related.  It just seems easier - everything outside of Ubuntu respects either the path, or JAVA_HOME.[/quote]

This is my opinion and I may be way off, but I think the eventual goal is to have all java apps in the ubuntu repositories respecting the java-alternatives settings.  For now though, it is definitely a pain to have some applications respecting it, while others use there own CLASSPATH settings.  Maybe things will be better with Eft?

---

### Post by TehLiberating on 2006-07-01
Let's hope so, I've found that the hardest part of setting up Ubuntu after a reinstall is getting eclipse to work.

---

### Post by jvictor on 2006-07-01
Does your eclipse shutdown clean when u click exit.. For me the underlying Java process seems to be a resident evil in the memory till I do an explicit kill -9 <pid>

Ironically this is not the case if u run eclipse from the shell using the -vm argument pointing to GCJ. This happens only with Sun / Blackdown JDK.

I use the eclipse from eclipse.org and not the native one.


Can some plz chk it and confirm ?

---

### Post by hod139 on 2006-07-01
[quote=TehLiberating]Let's hope so, I've found that the hardest part of setting up Ubuntu after a reinstall is getting eclipse to work.[/quote] I wrote this [howto]("http://ubuntuforums.org/showthread.php?t=201378") which will hopefully make the install easier.

[quote=jvictor]
Does your eclipse shutdown clean when u click exit.. For me the underlying Java process seems to be a resident evil in the memory till I do an explicit kill -9 <pid>

Ironically this is not the case if u run eclipse from the shell using the -vm argument pointing to GCJ. This happens only with Sun / Blackdown JDK.

I use the eclipse from eclipse.org and not the native one.


Can some plz chk it and confirm ?
[/quote] 
Using the version of eclipse in the repository and the install instructions in my howto, eclipse cleanly shuts down.  I tried 
```
ps aux | grep java
ps aux | grep eclipse
``` both of which returned nothing running.

---

### Post by jvictor on 2006-07-02
Thanks it works fine now !

---

### Post by robertmcox on 2006-07-05
me too....

...Ubuntu is supposed to be "newb friendly", but it sure isn't on the Java front.

(sorry if this is considered flaming, but this thread looks like it turned into a poll suggesting that the package maintainers fix this problem)

---

### Post by tabun on 2006-07-20
I noticed with gcj-4.1 does not understand the -sourcepath switch.  It is not the same as the classpath switch as some people propose to say. gjdoc understands this for some odd reason.  Suffice to say, I haven't compile azureus yet but I am getting closer.  Install java-gnome, gcj-4.1 and glade and whatever dependencies that pop up.

I went to the java gnome tutorial and the compilations didn't work as documented in the tutorial but after tweaking the command-line I managed to not only get glade going but also awt, and swt also.  I have attached some source files and hope it nudges people in the right direction.  The more the merrier on this gcj stuff because it merits the attention.

Cheers,
tabun

---

### Post by tabun on 2006-07-20
I previously posted a tar gz file with the examples but to ensure everybody does actually see what I am talking about without downloading the tar.gz. I decided to post the sources straight in this post. the tar.gz is still available if you look at my previous post.

Here is the awt example and the ubuntu dapper command line:
gcj-4.1 --main=ExampleAWT -o ExampleAWT ExampleAWT.java

import java.awt.Frame;
import java.awt.Label;
import java.awt.Button;
import java.awt.Panel;
import java.awt.event.ActionEvent;
import java.awt.event.WindowEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowListener;
import java.awt.FlowLayout;
import java.awt.BorderLayout;
import java.awt.event.WindowAdapter;

public class ExampleAWT extends Frame {
 ExampleAWT() {
  super("AWT");
  Label msgLabel = new Label("Quit?");
  Button yesButton = new Button("Yes");
  Button noButton = new Button("No");
  Panel buttonbox = new Panel();
  buttonbox.setLayout(new FlowLayout());
  buttonbox.add(yesButton);
  buttonbox.add(noButton);
  Panel msgbox = new Panel();
  msgbox.setLayout(new FlowLayout());
  msgbox.add(msgLabel);
  add(msgbox, BorderLayout.NORTH);
  add(buttonbox, BorderLayout.SOUTH);
    
  yesButton.addActionListener(new ActionListener() {
   public void actionPerformed(ActionEvent e) {
    System.exit(0);
  }
  });
  noButton.addActionListener(new ActionListener() {
   public void actionPerformed(ActionEvent e) {
    System.exit(1);
   }
  });
  addWindowListener(new WindowAdapter() {
   public void windowClosing(WindowEvent e) {
     System.exit(0);
   }
  });
 }
 public static void main(String[] args) {
  ExampleAWT frame = new ExampleAWT();
  frame.pack();
  frame.setVisible(true);
 }
}



Here is the swt example and the ubuntu dapper command line:

//This is necessary for avoiding linker errors
export LD_LIBRARY_PATH=.:/usr/lib/gcj-4.1:/usr/lib/jni
gcj-4.1 -fjni -fPIC -shared -o libswt.so /usr/lib/java/swt.jar
gcj-4.1 --CLASSPATH=/usr/lib/java/swt.jar -L. -lswt --main=ExampleSWT -o ExampleSWT ExampleSWT.java




//./ExampleSWT
import org.eclipse.swt.widgets.Display;
import org.eclipse.swt.widgets.Shell;
import org.eclipse.swt.widgets.Composite;
import org.eclipse.swt.layout.RowLayout;
import org.eclipse.swt.widgets.Label;
import org.eclipse.swt.widgets.Button;
import org.eclipse.swt.events.SelectionEvent;
import org.eclipse.swt.SWT;
import org.eclipse.swt.layout.FillLayout;
import org.eclipse.swt.events.SelectionAdapter;

public class ExampleSWT {
 public static void main(String[] args) {
  Display display = new Display();
  Shell shell = new Shell(display);
  shell.setLayout(new FillLayout(SWT.VERTICAL));
  Composite msgbox = new Composite(shell, 
                                   SWT.NO_TRIM);
  RowLayout msglayout = new RowLayout();
  msglayout.justify = true;
  msgbox.setLayout(msglayout);
  Label label = new Label(msgbox, SWT.NO_TRIM);
  label.setText("Quit?");
  Composite buttonbox = new Composite(shell, 
                                      SWT.NO_TRIM);
  RowLayout buttonlayout = new RowLayout();
  buttonlayout.justify = true;
  buttonlayout.pack = true;
  buttonbox.setLayout(buttonlayout);
  Button yesButton = new Button(buttonbox,
                                SWT.PUSH); 
  yesButton.setText("Yes");
  Button noButton = new Button(buttonbox,
                               SWT.PUSH); 
  noButton.setText("No");
  yesButton.addSelectionListener(
                            new SelectionAdapter() {
   public void widgetSelected(
                             SelectionEvent event) {
    System.exit(0);
   }
  });
  noButton.addSelectionListener(
                            new SelectionAdapter() {
   public void widgetSelected(
                             SelectionEvent event) {
    System.exit(1);
   }
  });
    
  shell.pack();
  shell.open();
  while (! shell.isDisposed()) {
   if (! display.readAndDispatch()) display.sleep();
  }
 }
}






Here is the glade example and the ubuntu dapper command line:
export LD_LIBRARY_PATH=.:/usr/lib/gcj-4.1:/usr/lib/jni
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/glade2.12.jar -fjni -fPIC -shared -o libcairo.so /usr/share/java/cairo1.0.jar
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/glade2.12.jar -fjni -fPIC -shared -o libglib.so /usr/share/java/glib0.2.jar
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/glade2.12.jar -fjni -fPIC -shared -o libgtk.so /usr/share/java/gtk2.8.jar
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/gnome2.12.jar:/usr/share/java/glade2.12.jar -fjni -fPIC -shared -o libgnome.so /usr/share/java/gnome2.12.jar
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/gnome2.12.jar:/usr/share/java/glade2.12.jar -fjni -fPIC -shared -o libglade.so /usr/share/java/glade2.12.jar
gcj-4.1 --CLASSPATH=/usr/share/java/glib0.2.jar:/usr/share/java/cairo1.0.jar:/usr/share/java/gtk2.8.jar:/usr/share/java/gnome2.12.jar:/usr/share/java/glade2.12.jar -L. -lcairo -lglib -lgtk -lgnome -lglade --main=FirstGlade -o FirstGlade FirstGlade.java 







import java.io.FileNotFoundException;
import java.io.IOException;

import org.gnu.glade.GladeXMLException;
import org.gnu.glade.LibGlade;
import org.gnu.gtk.Gtk;
import org.gnu.gtk.Entry;
import org.gnu.gtk.Button;

public class FirstGlade
{
    private LibGlade firstApp;
    private Entry width;
    private Entry height;
    private Entry hypotenuse;
    private Button calculate;

    public FirstGlade() throws FileNotFoundException, GladeXMLException, IOException
    {
        firstApp = new LibGlade("first.glade", this);
	connectToWidgets();
    }

   private void connectToWidgets()
    {
        width = (Entry) firstApp.getWidget("entry1");
        height = (Entry) firstApp.getWidget("entry2");
        hypotenuse = (Entry) firstApp.getWidget("entry3");
        calculate = (Button) firstApp.getWidget("button1");
    }
    
    private double calculateHypotenuse()
    {
        double w = Double.parseDouble(width.getText());
        double h = Double.parseDouble(height.getText());
        return Math.sqrt(w * w + h * h);
    }
    
    public void on_button1_clicked()
    {
        hypotenuse.setText("" + calculateHypotenuse());
    }
    

    public void on_window1_delete_event()
    {
        Gtk.mainQuit();
    }
    
    public static void main(String[] args)
    {
        FirstGlade g;
        
        try {
            Gtk.init(args);
            g = new FirstGlade();
            Gtk.main();
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
}


You will find the glade project and gui files the previously posted tar.gz.  At least the above gives you a sense of what's in tar.gz file.

Cheers,
tabun

---

### Post by korny on 2006-07-25
Just to revive this thread - I think I've found a fairly simple workaround, though it needs a bit more thought.

Most java apps seem to either check the path (which works with update-alternatives) or the JAVA_HOME setting, before they go wild looking at /etc/jvm or whatever.

So I wrote a little bash script which sets JAVA_HOME according to the current path, assuming the path was set by update-alternatives; if you put this in a startup script such as .bashrc it should set JAVA_HOME even after a call to update-alternatives.  It won't work on existing shells though.

```
 #!/bin/bash
JAVA_LOC=$(which javac)
if [[ ! -f $JAVA_LOC ]]
then
  JAVA_LOC=$(which java)
fi
if [[ ! -f $JAVA_LOC ]]
then
  echo No java or javac in path - can't set JAVA_HOME
else
  export JAVA_HOME=$(dirname $(dirname $(readlink -f $JAVA_LOC) ) )
  echo JAVA_HOME now set to $JAVA_HOME
fi

``` 
Basically this finds the javac or java executable, resolves any symlinks to find the real location, then looks for the parent directory - so if javac is really /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/javac it will set JAVA_HOME to "/usr/lib/jvm/java-1.5.0-sun-1.5.0.06"

I'm not 100% sure this will work with the standard ubuntu java installs, when I find time I'm going to try this on a vanilla install with gcj and sun-java, and see if it fixes all the various synaptic-installed tools.

---

### Post by manuelgchacon on 2007-02-06
This is something that took me a while to get around as well.  I usually develop Java on a Mac or Windows box so I am a Linux/Ubuntu newbie.  I was expecting the ~/.bashrc or ~/.bash_profile JAVA_HOME setup to work just like it would on a UNIX box and I was ready to say *&^#&* Ubuntu right before I googled one last time and ran into this.  

[http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)

sudo apt-get install sun-java5-jdk

Can anybody tell me the benefits of having to install Java in this manner instead of using the standard .bin files ?

---

### Post by geakMonkey on 2007-02-25
> **korny said:**
> You misunderstand - I've set up java many many times on a wide range of platforms - but given it is now in a fairly mainstream apt package, I'd quite like it to be a seamless integration, so Java applications "just work" without needing manual tweaking.

Sure, *I* can get it working, but I'm not so certain about the vast body of new users who don't have a high level of experience with all this mess - they will have to rely on gleaning information from the long list of incorrect HOWTOs out there, or reverse-engineering shell scripts, or luck.

- Korny

Ditto minus Java Developer equals Noobie.

I am coming from the Mandrake world where I have been admining since '98 - last century. I work for a non-profit and we wanted to use Debian for years but our servers were updatable and maintainable until Mandrake bought Connectiva, which I am sure that is a great acquisition. But our servers began to break a bit. I needed to learn a new system and it became time to look at other options: either invest more time, effort, energy into learning Mand* or get closer to GNU communities to support the overall intention.

That all said, I "hate Java!!!"

But we use it so I have to install it. I spent four days pouring over the 1000+- HOWTOS starting with installing Dapper Java 1.4, 1.5, then 1.6. This week: I have learned more about Java since I worled in Tech Support at Borland next to the JBuilder section last century. I do not want to become a Java Developer to run necessary programs. 

I bought the books - everything but the t-shirt, hat, and keychain. Now, I want it to work.

I.e.; I tried out the apt-get * alternatives. I uninstalled gjc so that might be my problem, who knows? Yet, I cannot even get 

me@myworkstation# java 

I get,

me@myworkstation# java  
bash: java: command not found

???
Help...

---

### Post by korny on 2007-02-25
These days I do the following on a new ubuntu box:
- Install gcj (as several things have it as a dependency) from synaptic
- Install eclipse, ant, junit etc. from synaptic, unless I want to run a more recent version
- Install Sun java 1.5 following the instructions on the Ubuntu unofficial FAQ:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)
(this includes instructions on editing /etc/jvm)
- If I installed eclipse via synaptic, update the eclipse-special jvm config file (it's on the above faq as well, somewhere)

At this stage, 'java -version' should work, but JAVA_HOME is not set.
If I want to install/run an application that needs JAVA_HOME, I either set it manually in my .bashrc file, or I use the snippet I listed above to set it from the "javac" executable in the path.

Hope that helps!  I'd love to not have to install gcj, but several synaptic packages have it as a prerequisite, so I install it but never use it.

---

### Post by geakMonkey on 2007-02-26
Great!

This worked for my set-up:

update-java-alternatives -s java-1.5.0-sun

from the links above.

Thanks!!!:KS

---

