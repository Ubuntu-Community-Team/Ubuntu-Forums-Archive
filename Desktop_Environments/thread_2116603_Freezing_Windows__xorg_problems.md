---
title: "Freezing Windows / xorg problems?"
date: 2013-02-16
forum: Desktop Environments
---

### Post by Pandanus on 2013-02-16
Dear Forum,

I know that I am supposed to keep the questions short, but I really don't have a clue what the problem is, so please excuse me if I try to provide as much information as I can in the hope that someone comes up with an idea.
The general problem is that when my partner is using a certain program*1 after a while the desktop (lets say Unity for now, but see below) becomes unusable as all windows freeze; no closing or moving possible, only solution is to bring up a terminal and reboot, as restarting lightdm causes a hell of optical artifacts. This all looked like a graphics card problem*2 and after hunting around I found that there is a known bug with the nvidia drivers*3  and compiz, which fitted the problem extremely well, as I also got the same problem once when something was redrawing in a window. First I thought using normal gnome might do the trick as it only has to be changed at the login, but no luck. Therefore I thought I remove compiz from the equation by using xfce, installed xfce and all xubuntu stuff next to Ubuntu and got everything nicely set up, but just an hour ago the same freeze in xfce! As far as I know there should be no compiz involved in an xfce session and ps -e | grep compiz doesn't show anything... I am plainly lost, I do plainly not really know enough about (X)Ubuntu to decide were else to look. Perhaps one question if missing .desktop files could cause something like that as in .xsession-errors  a lot of warnings pop up, as the .ab1 (the trace files from the ABI sequencer) have no .desktop files (no idea why they should), and I also dont understand the rest of the Warnings in the .xsession-errors, perhaps ideas here could help as well.
Really sorry for the long post, but this all really has put a damper on my Ubuntu experience, especially convincing other people that this is a good alternative is difficult if the desktop environment just becomes so critically unusable.
Perhaps I should mention that I made a restricted account for my partner where she can run her programs (not in sudoers), no idea if this might make a difference.

Any help or suggestions will be very welcome
Cheers
Pandanus  


*1 seqtrace (sequence alignment software written in python [https://code.google.com/p/seqtrace/](https://code.google.com/p/seqtrace/))
*2 lspci | grep VGA
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)
```*3 [https://bugs.launchpad.net/compiz/0.9.8/+bug/1027211](https://bugs.launchpad.net/compiz/0.9.8/+bug/1027211)

uname -a
```
Linux Desktop-JT 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```The .xsession-errors from the login in question
(up to line 821 the .desktop file warnings for the .ab1 files and
from 823 the criticals I don't understand):
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0

(polkit-gnome-authentication-agent-1:9820): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:9820): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(xfce4-settings-helper:9847): xfce4-settings-helper-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:9932): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:9932): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:9932): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:9932): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:9932): Indicator-Application-WARNING **: Unable to get application list: Operation was cancelled

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/ITStrnLplate0810.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Crappyplate.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/PL_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/PL_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/NA_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/NA_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/NA_001_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/NA_001_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/HO_002_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/HO_002_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/GS_003_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/GS_003_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_003_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_003_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_002_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_002_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_001_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/ET_001_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/EL_002_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/EL_002_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_096_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_096_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_096_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_096_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_095_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_095_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_093_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_093_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_088_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_088_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_088_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_088_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_087_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_087_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_087_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_087_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_084_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_081_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_084_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_081_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_079_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_079_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_076_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_076_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_074_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_074_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_073_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_073_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_069_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_069_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_069_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_067_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_069_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_067_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_066_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_066_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_066_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_066_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_064_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_064_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_063_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_063_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_060_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_060_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_056_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_056_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_051_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_051_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_050_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_050_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_045_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_045_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_044_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_043_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_043_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_041_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_041_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_034_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_034_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_022_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_022_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_021_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_021_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_018_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_015_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_018_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_011_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_015_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_011_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_007_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_007_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_006_matK_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_006_matK_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_004_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AM_004_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/Am_044_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AL_002_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912/AL_002_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/trnL_At109_matK_270912" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ZI_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ZI_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_002_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_002_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_002_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_002_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/PL_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/NA_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/NA_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/HO_002_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/HO_002_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/HE_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/HE_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/GS_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/GS_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_003_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_003_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_002_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_002_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/ET_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/EA_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/EA_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/EA_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/EA_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_096_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_096_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_095_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_095_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_094_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_094_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_091_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_091_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_085_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_085_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_084_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_084_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_083_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_083_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_079_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_079_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_079_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_079_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_076_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_076_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_070_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_070_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_069_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_069_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_066_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_066_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_063_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_063_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_061_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_061_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_056_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_056_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_055_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_055_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_052_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_052_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_049_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_049_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_037_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_037_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_030_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_030_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_027_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_027_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_026_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_026_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_022_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_022_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_018_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_018_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_012_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_012_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_009_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_009_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_009_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_009_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_003_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_003_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_003_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_002_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_003_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_003_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AM_002_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_003_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_002_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_002_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_001_trnL_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_001_trnL_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912/AL_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/ITS_trnL_270912" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/121008NE-022" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/rpS16plate2409.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_069_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/HO_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_003_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/HO_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/ET_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/PL_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/PL_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/PL_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/PL_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/HO_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/HO_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/ET_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_013_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_003_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GS_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_044_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GC_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/GC_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_032_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_008_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/ET_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/ET_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_094_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/EL_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/EL_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/EL_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_090_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/EL_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_094_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_091_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_090_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_091_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_089_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_089_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_084_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_075_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_084_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_075_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_070_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_065_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_070_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_069_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_065_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_062_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_062_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_055_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_045_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_051_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_055_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_051_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_046_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_046_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_045_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_044_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_043_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_033_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_043_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_040_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_039_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_039_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_040_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_038_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_038_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_033_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_030_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_022_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_032_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_013_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_030_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_012_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_023_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_023_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_022_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_006_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_019_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_019_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_008_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_003_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_006_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_012_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AL_002_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_011_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AL_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_011_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_003_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AM_001_rpS16_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AL_002_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912/AL_001_rpS16_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/rpS16plate210912" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ZI_001_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ZI_001_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/PL_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/PL_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/PL_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/PL_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/NA_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/NA_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/HO_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/HO_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/GS_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/GS_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/GC_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/GC_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_003_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_003_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/ET_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_003_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_003_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/EL_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_095_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_095_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_094_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_094_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_090_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_090_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_084_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_084_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_075_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_075_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_070_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_070_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_068_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_068_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_065_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_065_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_061_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_061_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_055_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_055_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_051_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_051_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_049_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_049_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_045_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_045_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_044_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_044_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_043_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_043_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_040_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_040_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_039_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_039_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_038_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_038_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_033_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_033_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_032_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_032_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_030_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_030_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_027_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_027_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_022_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_022_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_019_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_019_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_017_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_017_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_013_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_012_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_013_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_012_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_011_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_009_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_011_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_009_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_006_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_006_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AM_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_004_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_004_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_003_ITS_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_003_ITS_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_002_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_002_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_001_At103_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912/AL_001_At103_F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/At103plate210912" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/ndhFplate2409.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/120912NR-001/Am_082_ndhF-1603_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/120912NR-001/Am_028_ndhF-803F.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/120912NR-001/Am_017_ndhF-1603_R.ab1" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/120912NR-001" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Trace%20files/120907NN-018" was not found, exec: seqtrace.py, mime_type: inode/directory

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Sequences_13_09_12.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

** (zeitgeist-datahub:9833): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/janie/Work/Amomum%20phylogenetics/Sequences/Sequences_from_13_09_12.str" was not found, exec: seqtrace.py, mime_type: application/octet-stream

(xfdesktop:9790): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-settings-manager:10074): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:9786): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(xfdesktop:9790): libxfce4ui-WARNING **: ICE I/O Error

(xfdesktop:9790): libxfce4ui-WARNING **: Disconnected from session manager.

(xfce4-settings-helper:9847): libxfce4ui-WARNING **: ICE I/O Error

(xfce4-panel:9786): libxfce4ui-WARNING **: ICE I/O Error

(xfce4-settings-helper:9847): libxfce4ui-WARNING **: Disconnected from session manager.

(xfce4-panel:9786): libxfce4ui-WARNING **: Disconnected from session manager.
** Message: PID 9823 (we are 9823) sent signal 15, shutting down...

** (zeitgeist-datahub:9833): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(nm-applet:9823): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed
xfce4-panel: Fatal IO error 4 (Interrupted system call) on X server :0.0.
xfdesktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```cat /var/log/Xorg.0.log | grep NVIDIA
```
[  6412.213] (II) Module glx: vendor="NVIDIA Corporation"
[  6412.213] (II) NVIDIA GLX Module  310.14  Tue Oct  9 12:14:30 PDT 2012
[  6412.215] (II) Module nvidia: vendor="NVIDIA Corporation"
[  6412.216] (II) Module nvidia: vendor="NVIDIA Corporation"
[  6412.218] (II) NVIDIA dlloader X Driver  310.14  Tue Oct  9 11:54:19 PDT 2012
[  6412.218] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  6412.218] (II) NOUVEAU driver for NVIDIA chipset families :
[  6412.218] (II) NVIDIA(0): Creating default Display subsection in Screen section
[  6412.218] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  6412.218] (==) NVIDIA(0): RGB weight 888
[  6412.218] (==) NVIDIA(0): Default visual is TrueColor
[  6412.219] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  6412.219] (**) NVIDIA(0): Option "NoLogo" "True"
[  6412.219] (**) NVIDIA(0): Enabling 2D acceleration
[  6412.696] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6412.696] (II) NVIDIA(GPU-0):     Vision stereo.
[  6412.697] (II) NVIDIA(0): NVIDIA GPU GeForce GT 520 (GF119) at PCI:1:0:0 (GPU-0)
[  6412.697] (--) NVIDIA(0): Memory: 1048576 kBytes
[  6412.697] (--) NVIDIA(0): VideoBIOS: 75.19.4c.00.01
[  6412.697] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  6412.708] (--) NVIDIA(0): Valid display device(s) on GeForce GT 520 at PCI:1:0:0
[  6412.708] (--) NVIDIA(0):     CRT-0
[  6412.708] (--) NVIDIA(0):     CRT-1
[  6412.708] (--) NVIDIA(0):     PKB Maestro223DXL (DFP-0) (connected)
[  6412.708] (--) NVIDIA(0):     DFP-1
[  6412.708] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[  6412.708] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[  6412.708] (--) NVIDIA(0): PKB Maestro223DXL (DFP-0): 330.0 MHz maximum pixel clock
[  6412.708] (--) NVIDIA(0): PKB Maestro223DXL (DFP-0): Internal Dual Link TMDS
[  6412.708] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[  6412.708] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[  6412.708] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6412.708] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6412.708] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6412.708] (==) NVIDIA(0): 
[  6412.708] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  6412.708] (==) NVIDIA(0):     will be used as the requested mode.
[  6412.708] (==) NVIDIA(0): 
[  6412.708] (II) NVIDIA(0): Validated MetaModes:
[  6412.708] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[  6412.708] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[  6412.752] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[  6412.752] (--) NVIDIA(0):     option
[  6412.752] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  6412.752] (II) NVIDIA:     access.
[  6412.769] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[  6412.817] (==) NVIDIA(0): Disabling shared memory pixmaps
[  6412.817] (==) NVIDIA(0): Backing store disabled
[  6412.817] (==) NVIDIA(0): Silken mouse enabled
[  6412.818] (==) NVIDIA(0): DPMS enabled
[  6412.818] (II) NVIDIA(0): [DRI2] Setup complete
[  6412.818] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  6413.220] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6413.220] (II) NVIDIA(GPU-0):     Vision stereo.
[  6413.220] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6413.220] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6413.220] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6413.323] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6413.323] (II) NVIDIA(GPU-0):     Vision stereo.
[  6413.323] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6413.323] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6413.323] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6420.362] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6420.362] (II) NVIDIA(GPU-0):     Vision stereo.
[  6420.362] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6420.362] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6420.362] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6420.554] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6420.554] (II) NVIDIA(GPU-0):     Vision stereo.
[  6420.554] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6420.554] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6420.554] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6420.682] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6420.682] (II) NVIDIA(GPU-0):     Vision stereo.
[  6420.682] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6420.682] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6420.682] (**) NVIDIA(0):     has been enabled on all display devices.)
[  6440.655] (II) NVIDIA(GPU-0): Display (PKB Maestro223DXL (DFP-0)) does not support NVIDIA 3D
[  6440.656] (II) NVIDIA(GPU-0):     Vision stereo.
[  6440.656] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6440.656] (**) NVIDIA(0):     device PKB Maestro223DXL (DFP-0) (Using EDID frequencies
[  6440.656] (**) NVIDIA(0):     has been enabled on all display devices.)
```

---

### Post by Pandanus on 2013-02-17
No suggestions yet? Even some hints about the .xsession-errors would be great.
At the moment I seem to have found a fix, at least no windows freeze yesterday, by disabling the compositor in Xfce:
*Settings ->  Settings Manager -> Window Manager Tweaks [tab Compositor] *un-tick "Enable display compositing"
 Will not mark the thread as solved yet, as I am still interested in the .xsession-errors, or other ideas what the problem actually  might be. (Or if it is worthwhile to file a bug report)

Regards
Pandanus

---

