---
title: "Netbeans/Java Crash"
date: 2005-11-06
forum: Desktop Environments
---

### Post by domstyledesign on 2005-11-06
When working with the Netbeans IDE, it crashes after performing certain actions.  It produces a log each time it happens, and it appears to either be a problem with libfontmanager.so, or some font on my machine.  does anyone know how i can fix this?

```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0e39ef6, pid=31150, tid=2965265328
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x31ef6]
#

---------------  T H R E A D  ---------------

Current thread (0x083e4460):  JavaThread "AWT-EventQueue-1" [_thread_in_native, id=31173]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0xabb8732c

Registers:
EAX=0xaaf46a58, EBX=0xb0e845a8, ECX=0xaaf46a58, EDX=0x000000b3
ESP=0xb0be3878, EBP=0xb0be38d0, ESI=0x00c408d4, EDI=0xaaf461d4
EIP=0xb0e39ef6, CR2=0xabb8732c, EFLAGS=0x00010202

Top of Stack: (sp=0xb0be3878)
0xb0be3878:   b0be3918 004a0235 b0be38a0 b0e3cc6d
0xb0be3888:   00000000 00004000 00004000 00004000
0xb0be3898:   b0e845a8 aaf47414 b0be38d0 b0e36c71
0xb0be38a8:   aaf461d4 aaf461d4 aaf426c8 00000000
0xb0be38b8:   00310235 00420224 7972746e b0e845a8
0xb0be38c8:   aaf42758 aaf4278c b0be38f0 b0e3cec6
0xb0be38d8:   b0be3918 00000000 0000000a b26bb690
0xb0be38e8:   b0e88ac0 b79bd7a8 b0be3a50 b0e3d24e 

Instructions: (pc=0xb0e39ef6)
0xb0e39ee6:   8d 14 85 00 00 00 00 8b 7d d8 8b 47 1c 8b 14 10
0xb0e39ef6:   8b 04 31 29 d0 89 44 24 04 8b 45 e8 8d 34 85 00 

Stack: [0xb0b65000,0xb0be6000),  sp=0xb0be3878,  free space=506k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x31ef6]
C  [libfontmanager.so+0x34ec6]
C  [libfontmanager.so+0x3524e]
C  [libfontmanager.so+0x3768a]
C  [libfontmanager.so+0x35a92]
C  [libfontmanager.so+0x35faa]
C  [libfontmanager.so+0x225c6]
C  [libfontmanager.so+0x24326]
C  [libfontmanager.so+0x463c6]  Java_sun_font_FileFont_getGlyphImage+0x120
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtrs([I[JI)V+92
J  sun.font.GlyphList.mapChars(Lsun/java2d/loops/FontInfo;I)Z
J  sun.font.GlyphList.setFromString(Lsun/java2d/loops/FontInfo;Ljava/lang/String;FF)Z
J  sun.java2d.pipe.GlyphListPipe.drawString(Lsun/java2d/SunGraphics2D;Ljava/lang/String;DD)V
J  sun.java2d.SunGraphics2D.drawString(Ljava/lang/String;II)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.netbeans.beaninfo.editors.FontEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+137
j  org.netbeans.modules.form.FormPropertyEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+15
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.delegatedPaint(Ljava/awt/Graphics;)V+150
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.paint(Ljava/awt/Graphics;)V+61
j  org.openide.explorer.propertysheet.ButtonPanel.paint(Ljava/awt/Graphics;)V+64
j  javax.swing.CellRendererPane.paintComponent(Ljava/awt/Graphics;Ljava/awt/Component;Ljava/awt/Container;IIIIZ)V+124
j  javax.swing.plaf.basic.BasicTableUI.paintCell(Ljava/awt/Graphics;Ljava/awt/Rectangle;II)V+110
j  javax.swing.plaf.basic.BasicTableUI.paintCells(Ljava/awt/Graphics;IIII)V+133
j  javax.swing.plaf.basic.BasicTableUI.paint(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V+244
J  javax.swing.plaf.ComponentUI.update(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JComponent.paintComponent(Ljava/awt/Graphics;)V+26
j  org.openide.explorer.propertysheet.BaseTable.paintComponent(Ljava/awt/Graphics;)V+2
j  org.openide.explorer.propertysheet.SheetTable.paintComponent(Ljava/awt/Graphics;)V+18
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.openide.explorer.propertysheet.BaseTable.paint(Ljava/awt/Graphics;)V+15
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
j  javax.swing.JViewport.paint(Ljava/awt/Graphics;)V+192
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JSplitPane.paintChildren(Ljava/awt/Graphics;)V+2
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JComponent.paintWithOffscreenBuffer(Ljavax/swing/JComponent;Ljava/awt/Graphics;IIIILjava/awt/Image;)V+174
j  javax.swing.JComponent.paintDoubleBuffered(Ljavax/swing/JComponent;Ljava/awt/Component;Ljava/awt/Graphics;IIII)Z+131
J  javax.swing.JComponent._paintImmediately(IIII)V
j  javax.swing.JComponent.paintImmediately(IIII)V+83
J  javax.swing.RepaintManager.paintDirtyRegions()V
j  javax.swing.SystemEventQueueUtilities$ComponentWorkRequest.run()V+32
j  java.awt.event.InvocationEvent.dispatch()V+47
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+26
J  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x16cb6c]
V  [libjvm.so+0x25f688]
V  [libjvm.so+0x16c3c5]
V  [libjvm.so+0x16c45e]
V  [libjvm.so+0x1d1ac5]
V  [libjvm.so+0x2bdf03]
V  [libjvm.so+0x260198]
C  [libpthread.so.0+0x5361]


***TRUNCATED FOR POST SIZE***


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
libc:glibc 2.3.5 NPTL 2.3.5 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.61 0.90 0.83

CPU:total 1 family 15, cmov, cx8, fxsr, mmx, sse, sse2, ht

Memory: 4k page, physical 499680k(6244k free), swap 1285160k(1066664k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_05-b05) for linux-x86, built on Aug 26 2005 16:24:31 by java_re with gcc 3.2.1-7a (J2SE release)
```

---

### Post by coldrick on 2005-11-06
Not seen that one before. What version of NetBeans? Are you trying to use some special look and feel? You have the right version of Java.

Regards,
David

---

### Post by domstyledesign on 2005-11-06
i have sun's jdk 1.5, Netbeans v4.1, and no special look & feel whatever.

maybe i should give the beta version a shot

---

### Post by coldrick on 2005-11-06
Sorta doubt a different version of nb would help - the error is actually occurring within the java runtime engine.

Might be worth reinstalling java.

Having said that, it looks even deeper. Worth running a memory check on your machine, perhaps?

Regards,
David

---

### Post by domstyledesign on 2005-11-06
i re-installed the JDK and the JRE, still broken :(

---

### Post by jvictor on 2005-11-06
try eclipse , netbeans is a PIT*

---

### Post by domstyledesign on 2005-11-07
the only real reason i got netbeans was for the gui designer, and i think you have to get a plugin for eclipse to do that.

---

### Post by domstyledesign on 2005-11-07
besides, if this is a problem with Java (and not just Netbeans), then it would probably be a good idea for me to fix it now, instead of just ignoring it.

---

### Post by ksenos on 2005-11-19
Hello there, I get exactly the same error but with netbeans 5 beta, I say exactly the same. I believe it has something to do with jvm :(. Did anyone a solution or a reason for this?

This is the error message I get
```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1173d03, pid=8872, tid=2884103088
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#

---------------  T H R E A D  ---------------

Current thread (0x0836a768):  JavaThread "AWT-EventQueue-1" [_thread_in_native, id=8896]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0xabd05574

Registers:
EAX=0xabcc5574, EBX=0xb11c15a8, ECX=0x00040000, EDX=0x00000004
ESP=0xabe7c684, EBP=0xabe7c6ac, ESI=0xabcc5574, EDI=0x00010000
EIP=0xb1173d03, CR2=0xabd05574, EFLAGS=0x00210206

Top of Stack: (sp=0xabe7c684)
0xabe7c684:   abe7c6f4 0427d08e 0427313c 0427d08e
0xabe7c694:   00040000 0000000a 04273140 b11c15a8
0xabe7c6a4:   abcf5f28 abcf5f5c abe7c6cc b1179ec6
0xabe7c6b4:   abe7c6f4 abe7c6d4 abe7c6f4 abf4ed50
0xabe7c6c4:   b11c5ac0 abcf6188 abe7c82c b117a24e
0xabe7c6d4:   abe7c6f4 abcc76b0 abcc7749 abf4ed5c
0xabe7c6e4:   abf4f124 abe7de90 0836a768 abe7c6f4
0xabe7c6f4:   abcc7e8c abcc7e8c abcc7e8c 40000000 

Instructions: (pc=0xb1173d03)
0xb1173cf3:   8d 14 85 00 00 00 00 8b 41 04 8b 14 10 8b 4d e8
0xb1173d03:   8b 04 0e 29 d0 89 44 24 04 8b 45 08 8b 50 04 89 

Stack: [0xabdfe000,0xabe7f000),  sp=0xabe7c684,  free space=505k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x2ed03]
C  [libfontmanager.so+0x34ec6]
C  [libfontmanager.so+0x3524e]
C  [libfontmanager.so+0x3768a]
C  [libfontmanager.so+0x35a92]
C  [libfontmanager.so+0x35faa]
C  [libfontmanager.so+0x225c6]
C  [libfontmanager.so+0x24326]
C  [libfontmanager.so+0x463c6]  Java_sun_font_FileFont_getGlyphImage+0x120
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtrs([I[JI)V+92
j  sun.font.GlyphList.mapChars(Lsun/java2d/loops/FontInfo;I)Z+37
j  sun.font.GlyphList.setFromString(Lsun/java2d/loops/FontInfo;Ljava/lang/String;FF)Z+47
j  sun.java2d.pipe.GlyphListPipe.drawString(Lsun/java2d/SunGraphics2D;Ljava/lang/String;DD)V+148
j  sun.java2d.SunGraphics2D.drawString(Ljava/lang/String;II)V+25
j  org.netbeans.beaninfo.editors.FontEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+137
j  org.netbeans.modules.form.FormPropertyEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+15
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.delegatedPaint(Ljava/awt/Graphics;)V+150
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.paint(Ljava/awt/Graphics;)V+61
j  org.openide.explorer.propertysheet.ButtonPanel.paint(Ljava/awt/Graphics;)V+64
j  javax.swing.CellRendererPane.paintComponent(Ljava/awt/Graphics;Ljava/awt/Component;Ljava/awt/Container;IIIIZ)V+124
j  javax.swing.plaf.basic.BasicTableUI.paintCell(Ljava/awt/Graphics;Ljava/awt/Rectangle;II)V+110
j  javax.swing.plaf.basic.BasicTableUI.paintCells(Ljava/awt/Graphics;IIII)V+133
j  javax.swing.plaf.basic.BasicTableUI.paint(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V+244
J  javax.swing.plaf.ComponentUI.update(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V
J  javax.swing.JComponent.paintComponent(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.openide.explorer.propertysheet.BaseTable.paintComponent(Ljava/awt/Graphics;)V+2
j  org.openide.explorer.propertysheet.SheetTable.paintComponent(Ljava/awt/Graphics;)V+18
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.openide.explorer.propertysheet.BaseTable.paint(Ljava/awt/Graphics;)V+15
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
j  javax.swing.JViewport.paint(Ljava/awt/Graphics;)V+192
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JSplitPane.paintChildren(Ljava/awt/Graphics;)V+2
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JComponent.paintWithOffscreenBuffer(Ljavax/swing/JComponent;Ljava/awt/Graphics;IIIILjava/awt/Image;)V+174
j  javax.swing.JComponent.paintDoubleBuffered(Ljavax/swing/JComponent;Ljava/awt/Component;Ljava/awt/Graphics;IIII)Z+131
J  javax.swing.JComponent._paintImmediately(IIII)V
j  javax.swing.JComponent.paintImmediately(IIII)V+83
J  javax.swing.RepaintManager.paintDirtyRegions()V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.SystemEventQueueUtilities$ComponentWorkRequest.run()V+32
j  java.awt.event.InvocationEvent.dispatch()V+47
J  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V
J  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x16cb6c]
V  [libjvm.so+0x25f688]
V  [libjvm.so+0x16c3c5]
V  [libjvm.so+0x16c45e]
V  [libjvm.so+0x1d1ac5]
V  [libjvm.so+0x2bdf03]
V  [libjvm.so+0x260198]
C  [libpthread.so.0+0x5361]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtrs([I[JI)V+92
j  sun.font.GlyphList.mapChars(Lsun/java2d/loops/FontInfo;I)Z+37
j  sun.font.GlyphList.setFromString(Lsun/java2d/loops/FontInfo;Ljava/lang/String;FF)Z+47
j  sun.java2d.pipe.GlyphListPipe.drawString(Lsun/java2d/SunGraphics2D;Ljava/lang/String;DD)V+148
j  sun.java2d.SunGraphics2D.drawString(Ljava/lang/String;II)V+25
j  org.netbeans.beaninfo.editors.FontEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+137
j  org.netbeans.modules.form.FormPropertyEditor.paintValue(Ljava/awt/Graphics;Ljava/awt/Rectangle;)V+15
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.delegatedPaint(Ljava/awt/Graphics;)V+150
j  org.openide.explorer.propertysheet.RendererFactory$StringRenderer.paint(Ljava/awt/Graphics;)V+61
j  org.openide.explorer.propertysheet.ButtonPanel.paint(Ljava/awt/Graphics;)V+64
j  javax.swing.CellRendererPane.paintComponent(Ljava/awt/Graphics;Ljava/awt/Component;Ljava/awt/Container;IIIIZ)V+124
j  javax.swing.plaf.basic.BasicTableUI.paintCell(Ljava/awt/Graphics;Ljava/awt/Rectangle;II)V+110
j  javax.swing.plaf.basic.BasicTableUI.paintCells(Ljava/awt/Graphics;IIII)V+133
j  javax.swing.plaf.basic.BasicTableUI.paint(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V+244
J  javax.swing.plaf.ComponentUI.update(Ljava/awt/Graphics;Ljavax/swing/JComponent;)V
J  javax.swing.JComponent.paintComponent(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.openide.explorer.propertysheet.BaseTable.paintComponent(Ljava/awt/Graphics;)V+2
j  org.openide.explorer.propertysheet.SheetTable.paintComponent(Ljava/awt/Graphics;)V+18
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  org.openide.explorer.propertysheet.BaseTable.paint(Ljava/awt/Graphics;)V+15
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
j  javax.swing.JViewport.paint(Ljava/awt/Graphics;)V+192
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JSplitPane.paintChildren(Ljava/awt/Graphics;)V+2
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paintChildren(Ljava/awt/Graphics;)V
J  javax.swing.JComponent.paint(Ljava/awt/Graphics;)V
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  javax.swing.JComponent.paintWithOffscreenBuffer(Ljavax/swing/JComponent;Ljava/awt/Graphics;IIIILjava/awt/Image;)V+174
j  javax.swing.JComponent.paintDoubleBuffered(Ljavax/swing/JComponent;Ljava/awt/Component;Ljava/awt/Graphics;IIII)Z+131
J  javax.swing.JComponent._paintImmediately(IIII)V
j  javax.swing.JComponent.paintImmediately(IIII)V+83

------------------TRUNCATED-------------------------------

VM Arguments:
jvm_args: -Djdk.home=/usr/lib/j2sdk1.5-sun -Dnetbeans.osenv=/tmp/nbenv.8840 -Dnetbeans.osenv.nullsep=true -Dnetbeans.dirs=:/opt/netbeans-5.0beta/bin/../nb5.0:/opt/netbeans-5.0beta/bin/../ide6:/opt/netbeans-5.0beta/bin/../enterprise2:/opt/netbeans-5.0beta/bin/../harness -Dnetbeans.home=/opt/netbeans-5.0beta/platform6 -Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade -Dnetbeans.accept_license_class=org.netbeans.license.AcceptLicense -Xms32m -Xmx128m -XX:PermSize=32m -XX:MaxPermSize=96m -ea -Dapple.laf.useScreenMenuBar=true
java_command: org.netbeans.Main --userdir /home/ksenos/.netbeans/5.0beta --branding nb

Environment Variables:
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
USERNAME=ksenos
LD_LIBRARY_PATH=/usr/lib/j2sdk1.5-sun/jre/lib/i386/client:/usr/lib/j2sdk1.5-sun/jre/lib/i386:/usr/lib/j2sdk1.5-sun/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x2ebc30], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x2ebc30], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x25e6c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x25e6c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x25e6c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x260a10], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x260440], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x260440], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x260440], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x260440], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
libc:glibc 2.3.5 NPTL 2.3.5 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.10 0.76 0.33

CPU:total 1 family 15, cmov, cx8, fxsr, mmx, sse, sse2, ht

Memory: 4k page, physical 905904k(364184k free), swap 987988k(987988k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_05-b05) for linux-x86, built on Aug 26 2005 16:24:31 by java_re with gcc 3.2.1-7a (J2SE release)


```

---

### Post by ksenos on 2005-11-20
It seems I'm lucky. I reinstalled jdk 1.5 and everything seems to be fine (with netbeans 5 beta 2 at least). The only thing I did differently was that I installed the jdk as root and not by using the sudo command. Could this have something to do with it?

---

