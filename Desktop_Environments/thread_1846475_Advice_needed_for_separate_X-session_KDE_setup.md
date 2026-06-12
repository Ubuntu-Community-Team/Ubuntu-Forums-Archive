---
title: "Advice needed for separate X-session KDE setup"
date: 2011-09-19
forum: Desktop Environments
---

### Post by BradNeuman on 2011-09-19
I have a bit of a unique setup and I'd love some advice or help about how to get it set up correctly.

I have a desktop with a monitor and a projector, which I use primarily as a TV / internet browser. From my desk I can see both the monitor and the projector, but from my couch I can only see the projector. I have a regular keyboard and mouse as well as a wireless set which I keep on the couch.

Ideally I would like to be able to use my desktop keyboard and mouse on both displays, and the wireless on on at least the projector. The biggest issue is that I can't use twinview because I can't see the monitor from the couch, so when windows randomly open up over on the monitor, I have to kind of move the mouse over and alt-click-drag randomly in the dark, hoping I get the window I wanted, or get up off the couch and look at the monitor, which we all know isn't a real option.

I've tried without success to do a separate X sessions setup and a MultiSeatX setup. My machine details are as follows:

ubuntu: 11.04 (natty)
graphics card: nvidia GeForce 880 GTS
kernel: 2.6.38-8-generic
other hardware: corei7 2600 and 16gb ram

I am running the proprietary drivers and have the latest kernel  and nvidia-common installed. I was able to set up multiple X-sessions but KDE didn't display any window decorations on the projector, which according to this thread:
[URL="http://forum.kde.org/viewtopic.php?f=67&t=94614"]http://forum.kde.org/viewtopic.php?f=67&t=94614
[/URL]which links to this bug:
[URL="https://bugs.kde.org/show_bug.cgi?id=156475"]https://bugs.kde.org/show_bug.cgi?id=156475
[/URL]KDE just doesn't really support this configuration.

Next I tried setting up multiseatx following this:
[URL="https://help.ubuntu.com/community/MultiseatX"]https://help.ubuntu.com/community/MultiseatX
[/URL]and again using this guide:
[URL="https://wiki.archlinux.org/index.php/Xorg_multiseat#Setting_up_Xorg"]https://wiki.archlinux.org/index.php/Xorg_multiseat#Setting_up_Xorg
[/URL]but with both of those setups I would get no x loading at all. The window would go black every now and then as if x were trying to start, but it would fail every time. I was pretty careful about setting the right device bus id's and such in each file, but nothing seemed to work. One this I wasn't sure about was that these guides both had separate BusIds for each "device", but I only have one graphics card. Does multiseatx only work with a separate graphics card per seat?


What I'd like to hear from this community is advice about what I should do. I can post more specifics about one of the approaches I tried if someone thinks there is a chance of getting it working. I really like KDE and use it on all my other computers, so I'd like to stick with that, but if another window manager is the best solution I would consider it.

Also, I'm not completely broke so I would definitely consider buying a second graphics card if it might solve this problem.

Thanks for reading my long post and I look forward to your responses!

---

### Post by sumski on 2011-09-20
Did you try this:
[https://bugs.kde.org/show_bug.cgi?id=256242#c19](https://bugs.kde.org/show_bug.cgi?id=256242#c19)

[https://projects.kde.org/projects/kde/kde-workspace/repository/revisions/299a78772b823d28cf3c48aff696cfb978d0ae7e](https://projects.kde.org/projects/kde/kde-workspace/repository/revisions/299a78772b823d28cf3c48aff696cfb978d0ae7e)

This commit should be in KDE 4.7, are you already using it it? Or do you have 4.6?

---

### Post by BradNeuman on 2011-09-20
Ah yes, I should have said, I am using KDE 4.6.2

When I get home I'll try to upgrade and see if this works. Thanks, it looks promising!

---

### Post by sumski on 2011-09-23
Brad, Debian has backported that patch to 4.6.5, so maybe it would be posiblle to apply it to 4.6.2


backport_kwin_multihead_improvements.diff
```
From: Alberto Mattea <alberto@mattea.info>
From: Modestas Vainius <modax@debian.org>
Subject: Add basic multihead support to kwin
Origin: backport, commit:299a78772b823d28cf3c48aff696cfb978d0ae7e
Date: Sun May 8 20:39:27 2011 +0200
Last-Update: 2011-06-02
Bug: https://bugs.kde.org/256242
Applied-Upstream: 4.7

For now there is autostart support on all screens and support for different resolutions on different screens.
Keyboard shortcuts are still TODO
REVIEW: 101125
BUG: 256242

--- a/ksmserver/startup.cpp
+++ b/ksmserver/startup.cpp
@@ -161,10 +161,6 @@ void KSMServer::launchWM( const QList< Q
     wmProcess = startApplication( wmStartCommands[ 0 ], QString(), QString(), true );
     connect( wmProcess, SIGNAL( error( QProcess::ProcessError )), SLOT( wmProcessChange()));
     connect( wmProcess, SIGNAL( finished( int, QProcess::ExitStatus )), SLOT( wmProcessChange()));
-    // there can be possibly more wm's (because of forking for multihead),
-    // but in such case care only about the process of the first one
-    for (int i = 1; i < wmStartCommands.count(); i++)
-        startApplication( wmStartCommands[i] );
     QTimer::singleShot( 4000, this, SLOT( autoStart0() ) );
 }
 
--- a/kwin/geometry.cpp
+++ b/kwin/geometry.cpp
@@ -55,6 +55,9 @@ namespace KWin
 // Workspace
 //********************************************
 
+extern int screen_number;
+extern bool is_multihead;
+
 /*!
   Resizes the workspace after an XRANDR screen size change
  */
@@ -250,56 +253,89 @@ void Workspace::updateClientArea()
 
   \sa geometry()
  */
+
 QRect Workspace::clientArea( clientAreaOption opt, int screen, int desktop ) const
     {
     if( desktop == NETWinInfo::OnAllDesktops || desktop == 0 )
         desktop = currentDesktop();
     if( screen == -1 )
         screen = activeScreen();
-    
-    QRect sarea = (!screenarea.isEmpty() 
-            && screen < screenarea[ desktop ].size()) // screens may be missing during KWin initialization or screen config changes
-        ? screenarea[ desktop ][ screen ]
-        : Kephal::ScreenUtils::screenGeometry( screen );
-    QRect warea = workarea[ desktop ].isNull()
-        ? Kephal::ScreenUtils::desktopGeometry()
-        : workarea[ desktop ];
-    switch (opt)
-        {
-        case MaximizeArea:
-            if (options->xineramaMaximizeEnabled)
-                return sarea;
-            else
-                return warea;
-        case MaximizeFullArea:
-            if (options->xineramaMaximizeEnabled)
-                return Kephal::ScreenUtils::screenGeometry( screen );
-            else
-                return Kephal::ScreenUtils::desktopGeometry();
-        case FullScreenArea:
-            if (options->xineramaFullscreenEnabled)
-                return Kephal::ScreenUtils::screenGeometry( screen );
-            else
-                return Kephal::ScreenUtils::desktopGeometry();
-        case PlacementArea:
-            if (options->xineramaPlacementEnabled)
-                return sarea;
-            else
-                return warea;
-        case MovementArea:
-            if (options->xineramaMovementEnabled)
-                return Kephal::ScreenUtils::screenGeometry( screen );
-            else
-                return Kephal::ScreenUtils::desktopGeometry();
-        case WorkArea:
+
+    QRect sarea, warea;
+
+    if (is_multihead) {
+        sarea = (!screenarea.isEmpty()
+                   && screen < screenarea[ desktop ].size()) // screens may be missing during KWin initialization or screen config changes
+                  ? screenarea[ desktop ][ screen_number ]
+                  : Kephal::ScreenUtils::screenGeometry(screen_number);
+        warea = workarea[ desktop ].isNull()
+                ? Kephal::ScreenUtils::screenGeometry(screen_number)
+                : workarea[ desktop ];
+    } else {
+        sarea = (!screenarea.isEmpty()
+                && screen < screenarea[ desktop ].size()) // screens may be missing during KWin initialization or screen config changes
+                ? screenarea[ desktop ][ screen ]
+                : Kephal::ScreenUtils::screenGeometry(screen);
+        warea = workarea[ desktop ].isNull()
+                ? Kephal::ScreenUtils::desktopGeometry()
+                : workarea[ desktop ];
+    }
+
+    switch(opt) {
+    case MaximizeArea:
+        if (is_multihead)
+            return sarea;
+        else if (options->xineramaMaximizeEnabled)
+            return sarea;
+        else
             return warea;
-        case FullArea:
+    case MaximizeFullArea:
+        if (is_multihead)
+            return Kephal::ScreenUtils::screenGeometry(screen_number);
+        else if (options->xineramaMaximizeEnabled)
+            return Kephal::ScreenUtils::screenGeometry(screen);
+        else
             return Kephal::ScreenUtils::desktopGeometry();
-        case ScreenArea:
-            return Kephal::ScreenUtils::screenGeometry( screen );
-        }
-    abort();
+    case FullScreenArea:
+        if (is_multihead)
+            return Kephal::ScreenUtils::screenGeometry(screen_number);
+        else if (options->xineramaFullscreenEnabled)
+            return Kephal::ScreenUtils::screenGeometry(screen);
+        else
+            return Kephal::ScreenUtils::desktopGeometry();
+    case PlacementArea:
+        if (is_multihead)
+            return sarea;
+        else if (options->xineramaPlacementEnabled)
+            return sarea;
+        else
+            return warea;
+    case MovementArea:
+        if (is_multihead)
+            return Kephal::ScreenUtils::screenGeometry(screen_number);
+        else if (options->xineramaMovementEnabled)
+            return Kephal::ScreenUtils::screenGeometry(screen);
+        else
+            return Kephal::ScreenUtils::desktopGeometry();
+    case WorkArea:
+        if (is_multihead)
+            return sarea;
+        else
+            return warea;
+    case FullArea:
+        if (is_multihead)
+            return Kephal::ScreenUtils::screenGeometry(screen_number);
+        else
+            return Kephal::ScreenUtils::desktopGeometry();
+    case ScreenArea:
+        if (is_multihead)
+            return Kephal::ScreenUtils::screenGeometry(screen_number);
+        else
+            return Kephal::ScreenUtils::screenGeometry(screen);
     }
+    abort();
+}
+
 
 QRect Workspace::clientArea( clientAreaOption opt, const QPoint& p, int desktop ) const
     {
--- a/kwin/main.cpp
+++ b/kwin/main.cpp
@@ -74,6 +74,7 @@ Options* options;
 Atoms* atoms;
 
 int screen_number = -1;
+bool is_multihead = false;
 
 bool initting = false;
 
@@ -421,58 +422,47 @@ KDE_EXPORT int kdemain( int argc, char *
     // or command line settings to raster or OpenGL.
     QApplication::setGraphicsSystem("native");
 
-    if( !restored )
-        { // We only do the multihead fork if we are not restored by the session
-          // manager, since the session manager will register multiple kwins,
-          // one for each screen...
-        QByteArray multiHead = qgetenv( "KDE_MULTIHEAD" );
-        if( multiHead.toLower() == "true" )
-            {
-            Display* dpy = XOpenDisplay( NULL );
-            if( !dpy )
-                {
-                fprintf( stderr, "%s: FATAL ERROR while trying to open display %s\n",
-                    argv[0], XDisplayName( NULL ));
-                exit( 1 );
-                }
-
-            int number_of_screens = ScreenCount( dpy );
-            KWin::screen_number = DefaultScreen( dpy );
-            int pos; // Temporarily needed to reconstruct DISPLAY var if multi-head
-            QByteArray display_name = XDisplayString( dpy );
-            XCloseDisplay( dpy );
-            dpy = 0;
+    Display* dpy = XOpenDisplay(NULL);
+    if (!dpy) {
+        fprintf(stderr, "%s: FATAL ERROR while trying to open display %s\n",
+                argv[0], XDisplayName(NULL));
+        exit(1);
+    }
 
-            if(( pos = display_name.lastIndexOf( '.' )) != -1 )
-                display_name.remove( pos, 10 ); // 10 is enough to be sure we removed ".s"
+    int number_of_screens = ScreenCount(dpy);
 
-            QString envir;
-            if( number_of_screens != 1 )
-                {
-                for( int i = 0; i < number_of_screens; i++ )
-                    {
-                    // If execution doesn't pass by here, then kwin
-                    // acts exactly as previously
-                    if( i != KWin::screen_number && fork() == 0 )
-                        {
-                        KWin::screen_number = i;
-                        // Break here because we are the child process, we don't
-                        // want to fork() anymore
-                        break;
-                        }
-                    }
-                // In the next statement, display_name shouldn't contain a screen
-                // number. If it had it, it was removed at the "pos" check
-                envir.sprintf( "DISPLAY=%s.%d", display_name.data(), KWin::screen_number );
-
-                if( putenv( strdup( envir.toAscii() )))
-                    {
-                    fprintf( stderr, "%s: WARNING: unable to set DISPLAY environment variable\n", argv[0] );
-                    perror("putenv()");
-                    }
-                }
+    // multi head
+    if (number_of_screens != 1) {
+        KWin::is_multihead = true;
+        KWin::screen_number = DefaultScreen(dpy);
+        int pos; // Temporarily needed to reconstruct DISPLAY var if multi-head
+        QByteArray display_name = XDisplayString(dpy);
+        XCloseDisplay(dpy);
+        dpy = 0;
+
+        if ((pos = display_name.lastIndexOf('.')) != -1)
+            display_name.remove(pos, 10);   // 10 is enough to be sure we removed ".s"
+
+        QString envir;
+        for (int i = 0; i < number_of_screens; i++) {
+            // If execution doesn't pass by here, then kwin
+            // acts exactly as previously
+            if (i != KWin::screen_number && fork() == 0) {
+                KWin::screen_number = i;
+                // Break here because we are the child process, we don't
+                // want to fork() anymore
+                break;
             }
         }
+        // In the next statement, display_name shouldn't contain a screen
+        // number. If it had it, it was removed at the "pos" check
+        envir.sprintf("DISPLAY=%s.%d", display_name.data(), KWin::screen_number);
+
+        if (putenv(strdup(envir.toAscii()))) {
+            fprintf(stderr, "%s: WARNING: unable to set DISPLAY environment variable\n", argv[0]);
+            perror("putenv()");
+        }
+    }
 
     KAboutData aboutData(
         "kwin",                     // The program name used internally

```

---

### Post by BradNeuman on 2011-10-19
Thanks for your help guys. I got busy / lazy and never fixed this, but the upgrade to Oneric and KDE 4.7.1 fixed this problem, multiple x displays is working perfectly for me now

---

