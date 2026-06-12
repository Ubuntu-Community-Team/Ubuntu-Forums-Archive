---
title: "Launch Error"
date: 2021-09-19
forum: Desktop Environments
---

### Post by him610 on 2021-09-19
Can not open folder or file from Desktop. Error message reads, The folder could not be opened. Failed to execute child process "/usr/lib/x86_64-linux-gnu/xfce4/-exo-2/exo-helper/02" (No such file or directory)

```
$ inxi -SMC
System:
  Host: h270m Kernel: 5.11.0-25-generic x86_64 bits: 64 Desktop: Xfce 4.16.0 
  Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASRock model: H270M-ITX/ac serial: <superuser/root required> 
  UEFI: American Megatrends v: P2.50 date: 03/16/2018 
CPU:
  Topology: Dual Core model: Intel Pentium G4560 bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 800 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 

```
Behavior was noted on two different computers since upgrading to LTS 20.04.3.

[https://imgur.com/NcNs6cW.png]("https://imgur.com/NcNs6cW.png")

---

### Post by &amp;KyT$0P# on 2021-09-22
Please post the output from running this command in Terminal -
```
apt-cache policy libexo-2-0
```

---

### Post by him610 on 2021-09-22
```

hugh@b450m:~$ apt-cache policy libexo-2-0
libexo-2-0:
  Installed: 0.12.11-1ubuntu1.20.04.1
  Candidate: 0.12.11-1ubuntu1.20.04.1
  Version table:
 *** 0.12.11-1ubuntu1.20.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.12.11-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```
@halogen2, thanks for the suggestion. I was beginning to think no one was around.

---

### Post by &amp;KyT$0P# on 2021-09-22
Does 
```
ls -la /usr/lib/x86_64-linux-gnu/xfce4/exo-2
```
show [FONT=Courier New]exo-helper-2[/FONT] there and executable?

If so, what happens if you run that program directly in a Terminal -
```
/usr/lib/x86_64-linux-gnu/xfce4/exo-2/exo-helper-2
```
(I get a help message.)

---

### Post by him610 on 2021-09-23
Yes to both questions on one machine.
```

hugh@b450m:~$ ls -la /usr/lib/x86_64-linux-gnu/xfce4/exo-2
total 51
drwxr-xr-x 2 root root     3 Apr 19 08:21 ./
drwxr-xr-x 9 root root     9 Feb  9  2021 ../
-rwxr-xr-x 1 root root 80256 Mar 14  2021 exo-helper-2*

```
```
hugh@b450m:~$ /usr/lib/x86_64-linux-gnu/xfce4/exo-2/exo-helper-2
Usage:
  exo-helper-2 [OPTION…]

Help Options:
  -h, --help                        Show help options
  --help-all                        Show all help options
  --help-gtk                        Show GTK+ Options

GTK+ Options
  --class=CLASS                     Program class as used by the window manager
  --name=NAME                       Program name as used by the window manager
  --gdk-debug=FLAGS                 GDK debugging flags to set
  --gdk-no-debug=FLAGS              GDK debugging flags to unset
  --gtk-module=MODULES              Load additional GTK+ modules
  --g-fatal-warnings                Make all warnings fatal
  --gtk-debug=FLAGS                 GTK+ debugging flags to set
  --gtk-no-debug=FLAGS              GTK+ debugging flags to unset

Application Options:
  -V, --version                     Print version information and exit
  -c, --configure                   Open the Preferred Applications
configuration dialog
  -s, --socket-id=SOCKET ID         Settings manager socket
  -l, --launch=TYPE [PARAMETER]     Launch the default helper of TYPE with the optional PARAMETER, where TYPE is one of the following values.
  -q, --query=TYPE [PARAMETER]      Query the default helper of TYPE, where TYPE is one of the following values.
  --display=DISPLAY                 X display to use

The following TYPEs are supported for the --launch and --query commands:

  WebBrowser       - The preferred Web Browser.
  MailReader       - The preferred Mail Reader.
  FileManager      - The preferred File Manager.
  TerminalEmulator - The preferred Terminal Emulator.

```
However, on a second machine, I get not found to the first question.

---

### Post by him610 on 2021-09-23
> However, on a second machine, I get not found to the first question.
```
hugh@h270m:~/Desktop$ ls -la /usr/lib/x86_64-linux-gnu/xfce4/exo-2
ls: cannot access '/usr/lib/x86_64-linux-gnu/xfce4/exo-2': No such file or directory

```
Note: on first machine, b450m, I reinstalled* xfce4* while attempting to trackdown and correct problem before asking for help from Forum.

---

### Post by &amp;KyT$0P# on 2021-09-23
Does it make any difference if you do
```
sudo apt-get --reinstall install libexo-2-0
```
and then reboot?

---

### Post by him610 on 2021-09-23
No, it made no difference. 
I have discovered that I can open files on the Desktop, but I can not open folders/directories like Home, File System, nor other drives.
Other odd behavior - there is no ikon for xfce4-terminal in the whisker menu. It does not turn up when searching from the Whisker search bar nor Catfish.The only way to open it is right-click on the desktop then select *Open Terminal Here*. Maybe the two issues are related?
I have never experienced any issues like this ever since I have been using Ubuntu (Breezy Badger.)

---

### Post by &amp;KyT$0P# on 2021-09-24
In Xfce Settings > Preferred Applications > Utilities, what do you have set as File Manager?  Can you run that application from Terminal?

---

### Post by him610 on 2021-09-25
Thanks for hanging in there and continuing to assist.
> In Xfce Settings > Preferred Applications > Utilities, what do you have set as File Manager? Can you run that application from Terminal?
*xfce settings* - there is none; only *xfce terminal settings*
To answer your question about file manager: it is *thunar*, and I can initiate it from terminal command line.

To clarify: I followed your suggested string on another machine, I can follow it (Settings > Preferred Applications > Utilities); however, on this machine, h270m, there is no way to traverse from Settings > Preferred Applications as *Preferred Applications* is not present in the Settings dropdown list

---

### Post by him610 on 2021-09-26
> Can not open folder or file from Desktop.
This was my original issue from Post #1. It seems to have been corrected somehow; possibly, with a software update earlier today. I can not fully explain it, but after several days I can now open folders on the desktop by a double left mouse click with no more error messages appearing. I will be closing this issue.
 
@halogen2 - thanks for the help.

---

