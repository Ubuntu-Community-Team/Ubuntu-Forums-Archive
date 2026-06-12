---
title: "Run command when dvd inserted"
date: 2015-01-21
forum: Desktop Environments
---

### Post by MACscr on 2015-01-21
I automatically want to run: '/usr/bin/vlc --fullscreen dvd:///dev/sr0' when a dvd is inserted into my dvdrom. How can I accomplish this easily with lxde?

---

### Post by CantankRus on 2015-01-22
I have never used this but in the repos there is an application **cdde**.
> CDDE is a program that detects when a CD/DVD-ROM drive has a disc
inserted. When it finds a disc inserted in the drive it will attempt to
determine the type of the disc, and execute a specified command. This
means a DVD can be inserted and your favorite DVD software will start, or
a data CD can be automatically mounted, etc. The commands are defined in a
configuration file that has simple XML syntax.

You need to run **cdde** initially so it can create a config @  **~/.cdde.xml **
eg
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **cdde**
Error: Config file /home/glen/.cdde.xml does not exist!
I created a template configuration file located at /home/glen/.cdde.xml
I suggest you edit it to make sure the values are useful before you run cdde again.
```
Open the config in your text editor and check the drive path and insert your command in the appropriate line.
eg
```
<?xml version="1.0"?>
<cdde delay="5000000">
  <drive path="[COLOR="#FF0000"]/dev/cdrom[/COLOR]">
    <audio command="echo An audio cd was inserted."/>
    <data command="echo A data cd was inserted."/>
    <dvd command="[COLOR="#FF0000"]echo A dvd was inserted.[/COLOR]"/>
    <vcd command="echo A vcd was inserted."/>
    <svcd command="echo A svcd was inserted."/>
    <blank command="echo A blank cdr/dvdr was inserted."/>
    <mixed command="echo A mixed (audio/data) cd was inserted."/>
  </drive>
</cdde>
```

You will need to add "**cdde**" to your autostart list.
I don't have a dvd player here to test if it works or not.

---

