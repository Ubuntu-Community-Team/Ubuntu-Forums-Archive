---
title: "How do you compile JPC emulator in Ubuntu?"
date: 2009-06-21
forum: General Help
---

### Post by tm222 on 2009-06-21
I have tried and can't compile it. How to do it? :confused:

---

### Post by michy99 on 2009-06-21
Can you explain what you have tried and what error messages you received? Also, JPC is available as an already compiled jar file. Have you tried using that instead?

---

### Post by tm222 on 2009-06-21
I want to compile it because I have edited the source, and renamed it BaldJPC. Instead of ODIN it runs Balder, which is based on FreeDOS 1.0. I cannot figure out where to "Javac the source files," as it says in the compiling README.

---

### Post by michy99 on 2009-06-21
Assuming you have java installed, you compile with```
javac sourcefile
```where 'sourcefile' is the name of the source file.

If you don't have java installed, you need to do that first.```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

### Post by tm222 on 2009-06-21
The problem is, there is tons of .java, or Java source files.

Sorry, got the file ext. wrong.

---

### Post by michy99 on 2009-06-21
There should be a main file, probably called jpc.class or something like that. Usually there is a readme file with instructions.

---

### Post by tm222 on 2009-06-21
I am just getting tons of errors, many files I have tried. The README isn't much help. Here it is:

JPC: x86 PC Hardware Emulator



Build Instructions.



1) You will need a Java Development Kit 1.5 or later.



2) Javac the source files under org (no external dependencies)



3) The BIOS used in JPC is the Bochs BIOS; see [http://bochs.sourceforge.net/](http://bochs.sourceforge.net/)



4) The VGA BIOS used in JPC is the Plex86/Bochs LGPL'd bios; see [http://www.nongnu.org/vgabios](http://www.nongnu.org/vgabios)



5) Ensure both BIOS files are in the root directory of the classpath (easy way; run JPC from the root of the directory where you expanded the files)



6) The test Floppy image "odin070.img" is from the Odin FreeDOS project; see [http://odin.fdos.org/](http://odin.fdos.org/)



7) To run JPC:

	java org.jpc.j2se.PCMonitor -fda odin070.img 



8) To run the JPC debugger: 

	java org.jpc.debugger.JPC -fda odin070.img



9) To run some games you might like to download, put them in a directory on your real computer and use JPC's ability to view a directory tree as a virtual FAT32 drive. For example, if some games are in "dosgames" in the directory where you expanded all the JPC files then type:

	java org.jpc.j2se.PCMonitor -fda odin070.img -hda dir:dosgames -boot fda



10) Have Fun! Please report bugs and contribute fixes and suggestions via our website:

	[www.physics.ox.ac.uk/jpc](www.physics.ox.ac.uk/jpc)

---

### Post by michy99 on 2009-06-21
Ok, I downloaded this thing to see what I could do with it. You are right, the instructions leave much to be desired. However, I think I figured it out. Make sure you are in the org directory and enter this:```
javac ./jpc/j2se/JPCApplication.java
```

---

### Post by tm222 on 2009-06-21
I got about 92 errors, and no .class files. I messed up in one of the other posts with the file types.

---

### Post by michy99 on 2009-06-21
Did you make sure you were in the JPCSource/org/ directory when you ran the command above? It compiled for me, and then I ran it from the main JPCSource/ directory with the command in the readme file.

Give me a sample of the errors you are getting.

---

### Post by tm222 on 2009-06-21
Here is every error message.


./jpc/j2se/JPCApplication.java:46: package org.jpc.emulator.processor does not exist
import org.jpc.emulator.processor.*;
^
./jpc/j2se/JPCApplication.java:47: package org.jpc.emulator does not exist
import org.jpc.emulator.*;
^
./jpc/j2se/JPCApplication.java:48: package org.jpc.support does not exist
import org.jpc.support.*;
^
./jpc/j2se/JPCApplication.java:49: package org.jpc.emulator.motherboard does not exist
import org.jpc.emulator.motherboard.*;
^
./jpc/j2se/JPCApplication.java:50: package org.jpc.emulator.memory does not exist
import org.jpc.emulator.memory.*;
^
./jpc/j2se/JPCApplication.java:51: package org.jpc.emulator.memory.codeblock does not exist
import org.jpc.emulator.memory.codeblock.*;
^
./jpc/j2se/JPCApplication.java:52: package org.jpc.emulator.peripheral does not exist
import org.jpc.emulator.peripheral.*;
^
./jpc/j2se/JPCApplication.java:53: package org.jpc.emulator.pci.peripheral does not exist
import org.jpc.emulator.pci.peripheral.*;
^
./jpc/j2se/JPCApplication.java:56: cannot find symbol
symbol: class PCMonitorFrame
public class JPCApplication extends PCMonitorFrame
                                    ^
./jpc/j2se/JPCApplication.java:82: cannot find symbol
symbol  : class PC
location: class org.jpc.j2se.JPCApplication
    public JPCApplication(String[] args, PC pc) throws Exception
                                         ^
./jpc/j2se/JPCApplication.java:84: cannot find symbol
symbol  : variable ArgProcessor
location: class org.jpc.j2se.JPCApplication
        super("BaldJPC - " + ArgProcessor.findArg(args, "hda" , null), pc, args);
                             ^
./jpc/j2se/JPCApplication.java:86: cannot find symbol
symbol  : variable ArgProcessor
location: class org.jpc.j2se.JPCApplication
        String snapShot = ArgProcessor.findArg(args, "ss" , null);
                          ^
./jpc/j2se/JPCApplication.java:94: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
            pc.getGraphicsCard().resizeDisplay(monitor);
                                               ^
./jpc/j2se/JPCApplication.java:95: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
            monitor.loadState(f);
            ^
./jpc/j2se/JPCApplication.java:99: cannot find symbol
symbol  : method getJMenuBar()
location: class org.jpc.j2se.JPCApplication
        JMenuBar bar = getJMenuBar();
                       ^
./jpc/j2se/JPCApplication.java:103: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        saveSnapshot.addActionListener(this);
                    ^
./jpc/j2se/JPCApplication.java:105: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        loadSnapshot.addActionListener(this);
                    ^
./jpc/j2se/JPCApplication.java:110: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        changeFloppyA.addActionListener(this);
                     ^
./jpc/j2se/JPCApplication.java:112: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        changeFloppyB.addActionListener(this);
                     ^
./jpc/j2se/JPCApplication.java:118: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        dosgamesImage.addActionListener(this);
                     ^
./jpc/j2se/JPCApplication.java:120: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        moregamesImage.addActionListener(this);
                      ^
./jpc/j2se/JPCApplication.java:122: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        mousegamesImage.addActionListener(this);
                       ^
./jpc/j2se/JPCApplication.java:128: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        load.addActionListener(this);
            ^
./jpc/j2se/JPCApplication.java:130: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        image.addActionListener(this);
             ^
./jpc/j2se/JPCApplication.java:135: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        gettingStarted.addActionListener(this);
                      ^
./jpc/j2se/JPCApplication.java:137: addActionListener(java.awt.event.ActionListener) in javax.swing.AbstractButton cannot be applied to (org.jpc.j2se.JPCApplication)
        aboutUs.addActionListener(this);
               ^
./jpc/j2se/JPCApplication.java:165: cannot find symbol
symbol  : method getMonitorPane()
location: class org.jpc.j2se.JPCApplication
        getMonitorPane().setViewportView(licence);
        ^
./jpc/j2se/JPCApplication.java:167: cannot find symbol
symbol  : class KeyTypingPanel
location: class org.jpc.j2se.JPCApplication
        getContentPane().add("South", new KeyTypingPanel(monitor));
                                          ^
./jpc/j2se/JPCApplication.java:167: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
        getContentPane().add("South", new KeyTypingPanel(monitor));
                                                         ^
./jpc/j2se/JPCApplication.java:167: cannot find symbol
symbol  : method getContentPane()
location: class org.jpc.j2se.JPCApplication
        getContentPane().add("South", new KeyTypingPanel(monitor));
        ^
./jpc/j2se/JPCApplication.java:169: cannot find symbol
symbol  : method getContentPane()
location: class org.jpc.j2se.JPCApplication
        getContentPane().validate();
        ^
./jpc/j2se/JPCApplication.java:174: cannot find symbol
symbol  : variable super
location: class org.jpc.j2se.JPCApplication
        super.start();
        ^
./jpc/j2se/JPCApplication.java:176: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
        getMonitorPane().setViewportView(monitor);
                                         ^
./jpc/j2se/JPCApplication.java:176: cannot find symbol
symbol  : method getMonitorPane()
location: class org.jpc.j2se.JPCApplication
        getMonitorPane().setViewportView(monitor);
        ^
./jpc/j2se/JPCApplication.java:177: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
        monitor.validate();
        ^
./jpc/j2se/JPCApplication.java:178: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
        monitor.requestFocus();
        ^
./jpc/j2se/JPCApplication.java:185: showOptionDialog(java.awt.Component,java.lang.Object,java.lang.String,int,int,javax.swing.Icon,java.lang.Object[],java.lang.Object) in javax.swing.JOptionPane cannot be applied to (org.jpc.j2se.JPCApplication,java.lang.String,java.lang.String,int,int,<nulltype>,java.lang.String[],java.lang.String)
            load = JOptionPane.showOptionDialog(this, "Selecting " + loadString + " now will cause BaldJPC to reboot. Are you sure you want to continue?", "Warning", JOptionPane.YES_NO_OPTION, JOptionPane.WARNING_MESSAGE, null, new String[] {"Continue","Cancel"}, "Continue");
                              ^
./jpc/j2se/JPCApplication.java:187: showOptionDialog(java.awt.Component,java.lang.Object,java.lang.String,int,int,javax.swing.Icon,java.lang.Object[],java.lang.Object) in javax.swing.JOptionPane cannot be applied to (org.jpc.j2se.JPCApplication,java.lang.String,java.lang.String,int,int,<nulltype>,java.lang.String[],java.lang.String)
            load = JOptionPane.showOptionDialog(this, "Selecting " + loadString + " now will lose the current state of BaldJPC. Are you sure you want to continue?", "Warning", JOptionPane.YES_NO_OPTION, JOptionPane.WARNING_MESSAGE, null, new String[] {"Continue","Cancel"}, "Continue");
                              ^
./jpc/j2se/JPCApplication.java:194: cannot find symbol
symbol  : method stop()
location: class org.jpc.j2se.JPCApplication
                stop();
                ^
./jpc/j2se/JPCApplication.java:198: showDialog(java.awt.Component,java.lang.String) in javax.swing.JFileChooser cannot be applied to (org.jpc.j2se.JPCApplication,<nulltype>)
                returnVal = fileChooser.showDialog(this, null);
                                       ^
./jpc/j2se/JPCApplication.java:225: cannot find symbol
symbol  : class SeekableIODevice
location: class org.jpc.j2se.JPCApplication
                        SeekableIODevice ioDevice = new FileBackedSeekableIODevice(outFile.getPath());
                        ^
./jpc/j2se/JPCApplication.java:225: cannot find symbol
symbol  : class FileBackedSeekableIODevice
location: class org.jpc.j2se.JPCApplication
                        SeekableIODevice ioDevice = new FileBackedSeekableIODevice(outFile.getPath());
                                                        ^
./jpc/j2se/JPCApplication.java:226: cannot find symbol
symbol  : class RawBlockDevice
location: class org.jpc.j2se.JPCApplication
                        pc.getDrives().setHardDrive(0, new RawBlockDevice(ioDevice));
                                                           ^
./jpc/j2se/JPCApplication.java:226: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                        pc.getDrives().setHardDrive(0, new RawBlockDevice(ioDevice));
                        ^
./jpc/j2se/JPCApplication.java:228: cannot find symbol
symbol  : method setTitle(java.lang.String)
location: class org.jpc.j2se.JPCApplication
                        setTitle("JPC - " + loadString);
                        ^
./jpc/j2se/JPCApplication.java:235: cannot find symbol
symbol  : class BlockDevice
location: class org.jpc.j2se.JPCApplication
                            BlockDevice hda = new TreeBlockDevice(file, true);
                            ^
./jpc/j2se/JPCApplication.java:235: cannot find symbol
symbol  : class TreeBlockDevice
location: class org.jpc.j2se.JPCApplication
                            BlockDevice hda = new TreeBlockDevice(file, true);
                                                  ^
./jpc/j2se/JPCApplication.java:236: cannot find symbol
symbol  : class DriveSet
location: class org.jpc.j2se.JPCApplication
                            DriveSet drives = pc.getDrives();
                            ^
./jpc/j2se/JPCApplication.java:236: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                            DriveSet drives = pc.getDrives();
                                              ^
./jpc/j2se/JPCApplication.java:238: cannot find symbol
symbol  : method setTitle(java.lang.String)
location: class org.jpc.j2se.JPCApplication
                            setTitle("JPC - " + file);
                            ^
./jpc/j2se/JPCApplication.java:244: cannot find symbol
symbol  : class BlockDevice
location: class org.jpc.j2se.JPCApplication
                            BlockDevice device = null;
                            ^
./jpc/j2se/JPCApplication.java:246: cannot find symbol
symbol  : class SeekableIODevice
location: class org.jpc.j2se.JPCApplication
                            SeekableIODevice ioDevice = (SeekableIODevice)(blockClass.newInstance());
                            ^
./jpc/j2se/JPCApplication.java:246: cannot find symbol
symbol  : class SeekableIODevice
location: class org.jpc.j2se.JPCApplication
                            SeekableIODevice ioDevice = (SeekableIODevice)(blockClass.newInstance());
                                                         ^
./jpc/j2se/JPCApplication.java:248: cannot find symbol
symbol  : class RawBlockDevice
location: class org.jpc.j2se.JPCApplication
                            device = new RawBlockDevice(ioDevice);
                                         ^
./jpc/j2se/JPCApplication.java:249: cannot find symbol
symbol  : class DriveSet
location: class org.jpc.j2se.JPCApplication
                            DriveSet drives = pc.getDrives();
                            ^
./jpc/j2se/JPCApplication.java:249: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                            DriveSet drives = pc.getDrives();
                                              ^
./jpc/j2se/JPCApplication.java:252: cannot find symbol
symbol  : method setTitle(java.lang.String)
location: class org.jpc.j2se.JPCApplication
                            setTitle("JPC - " + file);
                            ^
./jpc/j2se/JPCApplication.java:265: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                            pc.loadState(file);
                            ^
./jpc/j2se/JPCApplication.java:267: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
                            pc.getGraphicsCard().resizeDisplay(monitor);
                                                               ^
./jpc/j2se/JPCApplication.java:267: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                            pc.getGraphicsCard().resizeDisplay(monitor);
                            ^
./jpc/j2se/JPCApplication.java:268: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
                            monitor.loadState(file);
                            ^
./jpc/j2se/JPCApplication.java:277: cannot find symbol
symbol  : method showMessageDialog(org.jpc.j2se.JPCApplication,java.lang.String,java.lang.String,int,<nulltype>)
location: class javax.swing.JOptionPane
                    JOptionPane.showMessageDialog(this, "The directory you selected contains too many files. Try selecting a directory with fewer contents.", "Error loading directory", JOptionPane.ERROR_MESSAGE, null);
                               ^
./jpc/j2se/JPCApplication.java:286: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
            monitor.stopUpdateThread();
            ^
./jpc/j2se/JPCApplication.java:288: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                pc.reset();
                ^
./jpc/j2se/JPCApplication.java:289: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
            monitor.revalidate();
            ^
./jpc/j2se/JPCApplication.java:290: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
            monitor.requestFocus();
            ^
./jpc/j2se/JPCApplication.java:293: cannot find symbol
symbol  : method reset()
location: class org.jpc.j2se.JPCApplication
                reset();
                ^
./jpc/j2se/JPCApplication.java:300: cannot find symbol
symbol  : method stop()
location: class org.jpc.j2se.JPCApplication
            stop();
            ^
./jpc/j2se/JPCApplication.java:301: showDialog(java.awt.Component,java.lang.String) in javax.swing.JFileChooser cannot be applied to (org.jpc.j2se.JPCApplication,java.lang.String)
        int returnVal = snapshotChooser.showDialog(this, "Save JPC Snapshot");
                                       ^
./jpc/j2se/JPCApplication.java:310: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                pc.saveState(zip);
                ^
./jpc/j2se/JPCApplication.java:311: cannot find symbol
symbol  : variable monitor
location: class org.jpc.j2se.JPCApplication
                monitor.saveState(zip);
                ^
./jpc/j2se/JPCApplication.java:325: showOptionDialog(java.awt.Component,java.lang.Object,java.lang.String,int,int,javax.swing.Icon,java.lang.Object[],java.lang.Object) in javax.swing.JOptionPane cannot be applied to (org.jpc.j2se.JPCApplication,java.lang.String,java.lang.String,int,int,<nulltype>,java.lang.Object[],java.lang.Object)
        int i =JOptionPane.showOptionDialog(this, aboutUsText, "JPC info", JOptionPane.YES_NO_OPTION, JOptionPane.INFORMATION_MESSAGE, null, buttons, buttons[1]);
                          ^
./jpc/j2se/JPCApplication.java:346: showDialog(java.awt.Component,java.lang.String) in javax.swing.JFileChooser cannot be applied to (org.jpc.j2se.JPCApplication,java.lang.String)
        int returnVal = floppyImageChooser.showDialog(this, "Load Floppy Drive Image");
                                          ^
./jpc/j2se/JPCApplication.java:352: cannot find symbol
symbol  : class BlockDevice
location: class org.jpc.j2se.JPCApplication
                BlockDevice device = null;
                ^
./jpc/j2se/JPCApplication.java:354: cannot find symbol
symbol  : class SeekableIODevice
location: class org.jpc.j2se.JPCApplication
                SeekableIODevice ioDevice = (SeekableIODevice)(blockClass.newInstance());
                ^
./jpc/j2se/JPCApplication.java:354: cannot find symbol
symbol  : class SeekableIODevice
location: class org.jpc.j2se.JPCApplication
                SeekableIODevice ioDevice = (SeekableIODevice)(blockClass.newInstance());
                                             ^
./jpc/j2se/JPCApplication.java:356: cannot find symbol
symbol  : class RawBlockDevice
location: class org.jpc.j2se.JPCApplication
                device = new RawBlockDevice(ioDevice);
                             ^
./jpc/j2se/JPCApplication.java:357: cannot find symbol
symbol  : variable pc
location: class org.jpc.j2se.JPCApplication
                pc.setFloppy(device, i);
                ^
./jpc/j2se/JPCApplication.java:367: cannot find symbol
symbol  : variable super
location: class org.jpc.j2se.JPCApplication
        super.actionPerformed(evt);
        ^
./jpc/j2se/JPCApplication.java:369: cannot find symbol
symbol  : variable doubleSize
location: class org.jpc.j2se.JPCApplication
        if (evt.getSource() == doubleSize)
                               ^
./jpc/j2se/JPCApplication.java:371: cannot find symbol
symbol  : variable doubleSize
location: class org.jpc.j2se.JPCApplication
            if (doubleSize.isSelected())
                ^
./jpc/j2se/JPCApplication.java:372: cannot find symbol
symbol  : method setBounds(int,int,int,int)
location: class org.jpc.j2se.JPCApplication
                setBounds(100, 100, (WIDTH*2)+20, (HEIGHT*2)+70);
                ^
./jpc/j2se/JPCApplication.java:374: cannot find symbol
symbol  : method setBounds(int,int,int,int)
location: class org.jpc.j2se.JPCApplication
                setBounds(100, 100, WIDTH+20, HEIGHT+70);
                ^
./jpc/j2se/JPCApplication.java:402: cannot find symbol
symbol  : method stop()
location: class org.jpc.j2se.JPCApplication
            stop();
            ^
./jpc/j2se/JPCApplication.java:403: cannot find symbol
symbol  : method getMonitorPane()
location: class org.jpc.j2se.JPCApplication
            getMonitorPane().setViewportView(licence);
            ^
./jpc/j2se/JPCApplication.java:453: cannot find symbol
symbol  : class PC
location: class org.jpc.j2se.JPCApplication
        PC pc = PC.createPC(args, new VirtualClock()); 
        ^
./jpc/j2se/JPCApplication.java:453: cannot find symbol
symbol  : class VirtualClock
location: class org.jpc.j2se.JPCApplication
        PC pc = PC.createPC(args, new VirtualClock()); 
                                      ^
./jpc/j2se/JPCApplication.java:453: cannot find symbol
symbol  : variable PC
location: class org.jpc.j2se.JPCApplication
        PC pc = PC.createPC(args, new VirtualClock()); 
                ^
./jpc/j2se/JPCApplication.java:456: cannot find symbol
symbol  : method setBounds(int,int,int,int)
location: class org.jpc.j2se.JPCApplication
        app.setBounds(100, 100, WIDTH+20, HEIGHT+70);
           ^
./jpc/j2se/JPCApplication.java:459: cannot find symbol
symbol  : method setIconImage(java.awt.Image)
location: class org.jpc.j2se.JPCApplication
            app.setIconImage(Toolkit.getDefaultToolkit().getImage(ClassLoader.getSystemResource("resource/jpcicon.png")));
               ^
./jpc/j2se/JPCApplication.java:463: cannot find symbol
symbol  : method validate()
location: class org.jpc.j2se.JPCApplication
        app.validate();
           ^
./jpc/j2se/JPCApplication.java:464: cannot find symbol
symbol  : method setVisible(boolean)
location: class org.jpc.j2se.JPCApplication
        app.setVisible(true);
           ^
92 errors


I am going to try and compile the orginal version, not edited by me.

---

### Post by tm222 on 2009-06-21
I cannot even compile the orginal JPC. I am using a live usb of ubuntu, that saves settings from this webpage, [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") 
It has been working well.

---

### Post by michy99 on 2009-06-21
That looks like the errors I got when trying to compile from the wrong location. What directory are you in when you try to compile?

---

### Post by tm222 on 2009-06-21
I am in /home/ubuntu/BaldJPC/org.

---

### Post by michy99 on 2009-06-21
Well, I am out of ideas. Maybe someone else can help.

---

### Post by cubeist on 2009-06-21
I think it is because you are using a live version of ubuntu, you don't have the necessary tools to compile.

---

### Post by tm222 on 2009-06-21
> **cubeist said:**
> I think it is because you are using a live version of ubuntu, you don't have the necessary tools to compile.


I have the regular JDK though.

---

### Post by cubeist on 2009-06-21
I'm sorry, I don't have much experience with compiling for java, but can you run/compile other java programs without errors?

---

### Post by tm222 on 2009-06-21
No Idea. I'll try a hello world app.

michy99, is there a way I send the source to you, and have you compile it? I tried .tar.gz archiving it, but the file was too big.

---

### Post by tm222 on 2009-06-21
I can compile a java app. I tried with a Hello World app.

---

