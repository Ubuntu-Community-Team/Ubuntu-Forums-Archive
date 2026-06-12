---
title: "[SOLVED] Lock keyboard / mouse without locking screen?"
date: 2008-06-26
forum: Desktop Environments
---

### Post by aoakley on 2008-06-26
Hi, I have a two-year old daughter and a Dell Inspiron 1520 laptop running Ubuntu Hardy 8.04 . I would like to show videos on the laptop whilst my daughter can bash the keyboard/mouse/trackpad .

How do I lock the keyboard and mouse/trackpad but not lock the screen please?

I won't leave my daughter alone with the laptop, but I might be on the other side of the room. I don't want to be constantly pulling her away from the keyboard.

I'm not frightened of writing Bash scripts or Perl, if that makes any difference.

---

### Post by aoakley on 2008-06-26
Solved. Use Lock Keyboard For Baby:

[http://sourceforge.net/project/showfiles.php?group_id=184401&package_id=214498](http://sourceforge.net/project/showfiles.php?group_id=184401&package_id=214498)

This Perl script locks the keyboard. I've also written a patch for this which locks the mouse buttons. I've emailed the author so hopefully the Sourceforge version will be updated with my mouse-locking patch.

--- lock-keyboard-for-baby.pl.orig      2008-06-26 17:05:26.000000000 +0100
+++ lock-keyboard-for-baby.pl   2008-06-26 17:01:51.000000000 +0100
@@ -2,7 +2,7 @@
 use warnings;
 use strict;
 use Data::Dumper;
-my $datemod="2006/05/25";
+my $datemod="2008/07/26";
 my $defaultpassword="QuitNow";
 my $progname=$0;
 $progname =~ s%.*/%%g;
@@ -17,11 +17,13 @@
                          [-p|password thepassword]
                          [-stars|-visible|-visible=maxlen]
                          [-message]
+        [-withmouse]
                          [-help]
 
 $progname was written by:Chris Sincock 
 (this version $datemod)
 Copyright (C) 2006 Chris Sincock
+-withmouse option added 2008 Andrew Oakley under GPL
 
 This is free software; see the GNU GPL license for copying conditions.
 There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR
@@ -45,6 +47,7 @@
 my $true=1;
 my $false=0;
 my $noshow=$true;
+my $withmouse=$false;
 my $maxshownlength=30;
 my $defaults_changed=$false;
 my $defaults_changed_vis=$false;
@@ -77,6 +80,12 @@
     $noshow="stars";
     $defaults_changed=$true;
   }
+  elsif($arg =~ /^(-|--)(w|withmouse)$/i)
+  {
+    $withmouse=$true;
+    $defaults_changed=$true;
+    $defaults_changed_vis=$true;
+  }
   elsif($arg =~ /^(-|--)(v|vis|visible)(=(\d+)|)$/i)
   {
     $noshow=$false;
@@ -131,11 +140,24 @@
   {
     $l->set_text("keyboard grab failed");
   }
+  if($withmouse)
+  {
+    $grabstatus= Gtk2::Gdk->pointer_grab(
+        $gdkwin,$true,['button-press-mask','button-release-mask'],undef,undef,Gtk2::Gdk::X11->get_server_time($gdkwin) );
+    if($grabstatus ne "success")
+    {
+      $l->set_text("pointer grab failed");
+    }
+  }
 }
 
 sub do_ungrab()
 {
   Gtk2::Gdk->keyboard_ungrab(Gtk2::Gdk::X11->get_server_time($gdkwin));
+  if($withmouse)
+  {
+    Gtk2::Gdk->pointer_ungrab(Gtk2::Gdk::X11->get_server_time($gdkwin));
+  }
 }
 
 sub do_keypress(@)

---

### Post by diego125k on 2009-05-07
hi!, first of all sorry for my English and thanks to Google Translate :D

I tried this patch, but did not let me enter the unlock code and I had to restart the Pc
I solved it editing original script (without patch) and I added the option -mouse  
 After this, run the script locks the keyboard and mouse but no screen. It work ok.
hopefully this will help many people, it is my first posting here :P
below is the script I was like to my (in bold the new lines),
[COLOR=Red]DO NOT COPY[/COLOR], for some reason the wysywyg editor of the forum break it and does not work, then download the next link:[LOCK-KEYBOARD-FOR-BABY.PY.tar.gz]("http://sites.google.com/site/diego125k2/Home/lock-keyboard-for-baby.pl.tar.gz?attredirects=0") (I put the file on my google Site)

```
#!/bin/env perl 
use warnings; 
use strict; 
use Data::Dumper;
my $lastmod="2009/05/07"; 
my $datemod="2006/05/25"; 
my $defaultpassword="QuitNow"; 
my $progname=$0; 
$progname =~ s%.*/%%g; 
 
sub usage($) 
{ 
  my ($exitcode)=@_; 
 
  print STDERR <<END_OF_USAGE ; 
usage for $progname 
$progname [-xy=XX,YY] 
              [-p|password thepassword] 
              [-stars|-visible|-visible=maxlen] 
              [-message] 
              [-help]
              [-mouse] 
 
$progname was written by:Chris Sincock  
(this version $datemod) 
Copyright (C) 2006 Chris Sincock
(this version $lastmod)
Copyright (C) 2009 Diego Guerrero 
 
This is free software; see the GNU GPL license for copying conditions. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR 
A PARTICULAR PURPOSE 
 
 
If you specify -password or -stars it will default to not telling you 
 what password to type 
If you don't specify -password or -stars or -vis, it will tell you 
 what password to type and the password will be $defaultpassword 
 
You can clear whatever has already been typed by hitting <Return> 
END_OF_USAGE 
 
  exit($exitcode); 
} 
 
 
my $password=$defaultpassword; 
my $message="Type the password to quit\n:"; 
my $true=1; 
my $false=0; 
my $noshow=$true; 
my $maxshownlength=30; 
my $defaults_changed=$false; 
my $defaults_changed_vis=$false;
my $mouse=$false;
my $keyb=$false;
 
 
my @startpos=(0,0); 
 
while (@ARGV) 
{ 
  my $arg=shift @ARGV; 
  if($arg =~ /^-xy=(\d+),(\d+)$/i) 
  { 
    @startpos=($1,$2); 
  } 
  elsif($arg =~ /^(-|--)(h|help|usage|[?])$/i) 
  { 
    usage(0); 
  } 
  elsif($arg =~ /^(-|--)(p|pass|password)$/i) 
  { 
    if(!@ARGV) 
    { 
      print STDERR "missing argument\n"; 
      usage(-1); 
    } 
    $password=shift @ARGV; 
    $defaults_changed=$true; 
  } 
  elsif($arg =~ /^(-|--)(s|stars)$/i) 
  { 
    $noshow="stars"; 
    $defaults_changed=$true; 
  } 
  elsif($arg =~ /^(-|--)(v|vis|visible)(=(\d+)|)$/i) 
  { 
    $noshow=$false; 
    if(length($4)) 
    { 
      $maxshownlength=$4; 
    } 
    $defaults_changed=$true; 
    $defaults_changed_vis=$true; 
  } 
  elsif($arg =~ /^(-|--)(m|msg|message)$/i) 
  { 
    if(!@ARGV) 
    { 
      print STDERR "missing argument\n"; 
      usage(-1); 
    } 
    $message=shift @ARGV; 
    if(length($message)) 
    { 
      $message.="\n"; 
    } 
    $defaults_changed=$true; 
  }
  elsif($arg =~ /^(-|--)(mouse)$/i)
  {
    $mouse=$true;
  } 
  else 
  { 
    usage(-1); 
  } 
} 
if(!$defaults_changed) 
{ 
  $noshow=$false; 
} 
if((!$defaults_changed || $defaults_changed_vis)) 
{ 
  $message="Type '$password' to quit\n"; 
} 
 
use Gtk2 -init; 
my $w  = new Gtk2::Window -popup; 
my $l  = new Gtk2::Label $message; 
my $eb = new Gtk2::EventBox; 
my $gdkwin; 
my $grabstatus; 
my $typed=""; 
 
sub do_grab() 
{
  $grabstatus= Gtk2::Gdk->keyboard_grab( 
      $gdkwin,$true,Gtk2::Gdk::X11->get_server_time($gdkwin) ); 
  if($grabstatus ne "success") 
  { 
    $l->set_text("keyboard grab failed"); 
  }
  if($mouse)
  { 
    $grabstatus= Gtk2::Gdk->pointer_grab(
       $gdkwin,$true,['button-press-mask','button-release-mask'],undef,undef,Gtk2::Gdk::X11->get_server_time($gdkwin));
    if($grabstatus ne "success")
    {
      $l->set_text("pointer grab failed"); 
    }
  } 
} 
 
sub do_ungrab() 
{ 
  Gtk2::Gdk->keyboard_ungrab(Gtk2::Gdk::X11->get_server_time($gdkwin));
  if($mouse)
  {
    Gtk2::Gdk->pointer_ungrab(Gtk2::Gdk::X11->get_server_time($gdkwin));
  }  
} 
 
sub do_keypress(@) 
{ 
  my ($widg,$evt)=@_; 
  my $kv = $evt->keyval; 
  my $cs = Gtk2::Gdk->keyval_name($kv); 
 
  if($cs =~ /Return|Enter/) 
  { 
    if($typed eq $password) 
    { 
      do_ungrab(); 
      Gtk2->main_quit; 
    } 
    else 
    { 
      $typed=""; 
    } 
  } 
  elsif(length($cs) == 1 && $cs =~ /[[:print:]]/) 
  { 
    $typed .= $cs; 
  } 
  my $showtyped=$typed; 
  if($noshow eq "stars") 
  { 
    $showtyped =~ s/[^*]/*/g; 
  } 
  elsif($noshow) 
  { 
    $showtyped=""; 
  } 
  if(length($showtyped) > $maxshownlength) 
  { 
    $showtyped=substr($showtyped,0,$maxshownlength); 
  } 
  $l->set_text($message.$showtyped); 
} 
$w->add($eb); 
$eb->add($l); 
$w->add_events( [ qw(key_press_mask) ]); 
$w->signal_connect('key_press_event', \&do_keypress); 
$w->signal_connect('realize', sub { $w->window->move(@startpos); }); 
$w->signal_connect('map', sub { $gdkwin=$w->window; do_grab(); }); 
$w->show_all; 
Gtk2->main; 
```Decompres file linked above and then give this permissions to execute
```
tar xvzf lock-keyboard-for-baby.pl.tar.gz
```
```
chmod +x lock-keyboard-for-baby.pl
```that's all, to run type
```
perl lock-keyboard-for-baby.pl -mouse

```(lock keyboard and mouse)
```
perl lock-keyboard-for-baby.pl

```(lock keyboard, dont lock mouse)

open source rocks:guitar:

---

### Post by megadevil on 2010-07-16
ehehe!
Thanks! It works perfectly!!!

---

### Post by changlinn on 2011-01-09
@diego125k: Thanks so much for this, took me all of ten minutes to google but kept my daughter busy while we packed away the TV and media centre.

---

### Post by stinkeye on 2011-01-09
There is xtrlock in the repos which locks the mouse and keyboard.
From man xtrloock
> DESCRIPTION
xtrlock locks the X server till the user enters their password at the keyboard. 

While xtrlock is running, the mouse and keyboard are grabbed and the mouse cursor becomes a padlock. Output displayed by X programs, and windows put up by new X clients, continue to be visible, and any new output is displayed normally. 

The mouse and keyboard are returned when the user types their password, followed by Enter or Newline. If an incorrect password is entered the bell is sounded. Pressing Backspace or Delete erases one character of a password partially typed; pressing Escape or Clear clears anything that has been entered. 

If too many attempts are made in too short a time further keystrokes generate bells and are otherwise ignored until a timeout has expired. 

The X server screen saver continues to operate normally; if it comes into operation the display may be restored by the usual means of touching a key (Shift, for example) or the mouse.  

---

### Post by suniljains on 2011-07-15
Gr8 Help!!

Thanks a lot!!

---

