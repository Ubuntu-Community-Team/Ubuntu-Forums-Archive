---
title: "ns2 error in running tcl files after successful installation"
date: 2009-08-06
forum: Education &amp; Science
---

### Post by yasirimteyaz on 2009-08-06
Hi,everyone.
I got a problem about running NS2 (2.33) on Ubuntu 9.04.
It got installed successfully without any errors.
I set-up all the PATHS.
after $ ns, i am getting the % sign
but when I enter the "ns simple.tcl" command ,the shell show this error below:

    (_o5 cmd line 1)
    invoked from within
"_o5 cmd at 1 “puts “Hello World!””"
    invoked from within
"catch "$self cmd $args" ret"
    invoked from within
"if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error "error when calling class $cls: $args" $..."
    (procedure "_o5" line 2)
    (SplitObject unknown line 2)
    invoked from within
"_o5 at 1 “puts “Hello World!””"
    ("eval" body line 1)
    invoked from within
"eval $scheduler_ at $args"
    (procedure "_o3" line 3)
    (Simulator at line 3)
    invoked from within
"$ns at 1 “puts \“Hello World!\””"
    (file "simple.tcl" line 2)
did anyone come across with the same problem?
If anyone know,could you help me.
thank you

---

### Post by yasirimteyaz on 2009-08-07
Whle running few example it does not print anything on terminal and return bact to $.
e.g.



yasir@yasir-laptop:~/Desktop$ ns
% 


yasir@yasir-laptop:~/ns-allinone-2.34/ns-2.34/tcl/mcast$ ns ns-lms.tcl 
yasir@yasir-laptop:~/ns-allinone-2.34/ns-2.34/tcl/mcast$ 


yasir@yasir-laptop:~/Desktop$ ns simple.tcl

    (_o5 cmd line 1)
    invoked from within
"_o5 cmd at 1 “puts “Hello World!””"
    invoked from within
"catch "$self cmd $args" ret"
    invoked from within
"if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error "error when calling class $cls: $args" $..."
    (procedure "_o5" line 2)
    (SplitObject unknown line 2)
    invoked from within
"_o5 at 1 “puts “Hello World!””"
    ("eval" body line 1)
    invoked from within
"eval $scheduler_ at $args"
    (procedure "_o3" line 3)
    (Simulator at line 3)
    invoked from within
"$ns at 1 “puts \“Hello World!\””"
    (file "simple.tcl" line 2)




**************simple.tcl***********
> set ns [new Simulator]
$ns at 1 “puts \“Hello World!\””
$ns at 1.5 “exit”
$ns run


---

### Post by yasirimteyaz on 2009-11-06
Got it working. :)

Check out my latest blog on installing ns2 on Ubuntu 9.10 [http://bit.ly/1DiXzB](http://bit.ly/1DiXzB)
It works perfectly with this method.

---

### Post by yasirjaved on 2009-11-27
After successfull installation and validation i run following script in example,tcl

#Create a simulator object
set ns [new Simulator]


#Open the NAM and Trace file
set nf [open out.nam w]
$ns namtrace-all $nf
set f0 [open out1.tr w]
$ns trace-all $f0


#Define different colors for data flows (for NAM)
$ns color 1 Blue
$ns color 2 Red


#Create six nodes
set n1 [$ns node]
set n2 [$ns node]
set n3 [$ns node]
set n4 [$ns node]
set n5 [$ns node]
set n6 [$ns node]



$ns duplex-link $n1 $n3 2Mb 10ms DropTail
$ns duplex-link $n2 $n3 2Mb 10ms DropTail
$ns duplex-link $n3 $n4 1Mb 10ms DropTail
$ns duplex-link $n4 $n5 2Mb 10ms DropTail
$ns duplex-link $n4 $n6 2Mb 10ms DropTail


$ns duplex-link-op $n1 $n3 orient right-down
$ns duplex-link-op $n2 $n3 orient right-up
$ns duplex-link-op $n3 $n4 orient right
$ns duplex-link-op $n4 $n5 orient right-up
$ns duplex-link-op $n4 $n6 orient right-down



#Set Queue Size of link (n3-n4) to 10
$ns queue-limit $n3 $n4 10


#Monitor the queue for link (n3-n4).
$ns duplex-link-op $n3 $n4 queuePos 0.5


#Setup a TCP connection
set tcp [new Agent/TCP/Reno]
#$tcp set packetsize_ 1000
$ns attach-agent $n1 $tcp
$tcp set class_ 1


set sink [new Agent/TCPSink]
$ns attach-agent $n5 $sink
$ns connect $tcp $sink


#Setup a FTP over TCP connection
set ftp [new Application/FTP]
$ftp attach-agent $tcp


#Setup a UDP connection
set udp [new Agent/UDP]
$ns attach-agent $n2 $udp
$udp set class_ 2

set null0 [new Agent/Null]
$ns attach-agent $n6 $null0
$ns connect $udp $null0


#Setup a CBR over UDP connection
set cbr0 [new Application/Traffic/CBR]
$cbr0 set packetSize_ 500
$cbr0 set interval_ 0.01
$cbr0 attach-agent $udp


#Schedule events for the CBR and FTP agents
$ns at 0.0 "$cbr0 start"
$ns at 0.0 "$ftp start"
$ns at 25.0 "$ftp stop"
$ns at 30.0 "$cbr0 stop"


#Define a 'finish' procedure
proc finish {} {
        global ns nf f0
        $ns flush-trace
        #Close the NAM trace file
        close $nf
        close $f0
        #Execute NAM on the trace file
        exec nam out.nam &
        exit 0
}


$ns at 30.0 "finish"


#Run the simulation
$ns run


---> Simulation writes trace and output files but no GUI window or graph is shown in which i could observe my output simulation. Plz can some body suggest a way out . I use ubuntu 9.04 and Ns-allinione-2.33

---

### Post by hisunnyvashistha on 2009-12-26
[U]I am having problems in installing ns2...please help me out..(thanking in advance)
This is what i tried......but failed to install ns2 .....
[/U]
sunny@sunny-laptop:~$ # LD_LIBRARY_PATH
sunny@sunny-laptop:~$ OTCL_LIB=/home?programmer/ns-allinone-2.34/otcl-1.13
sunny@sunny-laptop:~$ NS2_LIB=/home/programmer/ns-allinone-2.34/lib
sunny@sunny-laptop:~$ X11_LIB=/usr/X11R6/lib
sunny@sunny-laptop:~$ USR_LOCAL_LIB=/usr/local/lib
sunny@sunny-laptop:~$ export
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-JPNnwA3lVv,guid=b911744a0183856667d8cbe74b35df2a"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="default"
declare -x GDM_LANG="en_IN"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_KEYRING_PID="3268"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-8NvRE1/socket"
declare -x GPG_AGENT_INFO="/tmp/seahorse-KthSlA/S.gpg-agent:3362:1"
declare -x GTK_MODULES="canberra-gtk-module"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/sunny/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/sunny"
declare -x HTTP_PROXY="http://localhost:4001 "
declare -x LANG="en_IN"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="sunny"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x OLDPWD
declare -x ORBIT_SOCKETDIR="/tmp/orbit-sunny"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/sunny"
declare -x SESSION_MANAGER="local/sunny-laptop:/tmp/.ICE-unix/3280"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="3337"
declare -x SSH_AUTH_SOCK="/tmp/keyring-8NvRE1/socket.ssh"
declare -x TERM="xterm"
declare -x USER="sunny"
declare -x USERNAME="sunny"
declare -x WINDOWID="56623158"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/home/sunny/.Xauthority"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="14e43fcdcae526e3c6bd880f4a7f168d-1261821736.887664-258697618"
declare -x http_proxy="http://localhost:4001 "
sunny@sunny-laptop:~$ LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB:$X11_LIB:$USR_LOCAL_LIB
sunny@sunny-laptop:~$ #TCL_LIBRARY
sunny@sunny-laptop:~$ TCL_LIB=/home/programmer/ns-allinone-2.34/tcl8.4.18/library
sunny@sunny-laptop:~$ USR_LIB=/usr/lib
sunny@sunny-laptop:~$ export TCL_LIBRARY=$TCL_LIB:$USR_LIB
sunny@sunny-laptop:~$ #PATH
sunny@sunny-laptop:~$ XGRAPH=/home/programmer/ns-allinone-2.34/bin:/home/programmer/ns-allinone-2.34/tcl8.4.18/unix:/home/programmer/ns-allinone-2.34/tk8.4.18/unix:/home/programmer/ns-allinone-2.34/xgraph-12.1/NS=/home/programmer/ns-allinone-2.34/ns-2.34/NAM=/home/programmer/ns-allinone-2.34/nam-1.13/export PATH=$PATH:$XGRAPH:$NS:$NAM
sunny@sunny-laptop:~$ cd ns-2.34
bash: cd: ns-2.34: No such file or directory
sunny@sunny-laptop:~$ ./validate
bash: ./validate: No such file or directory
sunny@sunny-laptop:~$ sudo In-s/home/programmer/ns-allinone-2.34/ns-2.34/ns/usr/bin/ns
[sudo] password for sunny: 
sudo: In-s/home/programmer/ns-allinone-2.34/ns-2.34/ns/usr/bin/ns: command not found
sunny@sunny-laptop:~$ source ~/.bashrc
sunny@sunny-laptop:~$ ns
The program 'ns' is currently not installed.  You can install it by typing:
sudo apt-get install host
You will have to enable the component called 'universe'
bash: ns: command not found
sunny@sunny-laptop:~$ sudo apt-get install ns
[sudo] password for sunny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ns
sunny@sunny-laptop:~$ sudo apt-get install ns-2.34
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ns-2.34
sunny@sunny-laptop:~$ sudo apt-get install ns-allinone-2.34
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ns-allinone-2.34
sunny@sunny-laptop:~$ ---tk8.4.18-orig/generic/tkBind.c2006-07-21 08:26:54.000000000 +0200+++ tk8.4.18/generic/tkBind.c 2008-07-05 12:17:10.000000000 +0200@@ -586,6 +586,9 @@/*ColormapNotify*/COLORMAP,/*ClientMessage*/0,/*MappingNotify*/0,+#ifdef GenericEvent+/#endif/*VirtualEvent*/VIRTUAL,/*Activate*/ACTIVATE,/*Deactivate*/ACTIVATE,
bash: ---tk8.4.18-orig/generic/tkBind.c2006-07-21: No such file or directory
sunny@sunny-laptop:~$ ./install
bash: ./install: No such file or directory
sunny@sunny-laptop:~$ ./install ns-allinone-2.34
bash: ./install: No such file or directory
sunny@sunny-laptop:~$ sudo apt-get install build-essential autoconf automake libxmu-dev
[sudo] password for sunny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
sunny@sunny-laptop:~$ sudo cp/tmp/ns-allinone-2.34/usr/local
[sudo] password for sunny: 
Sorry, try again.
[sudo] password for sunny: 
sudo: cp/tmp/ns-allinone-2.34/usr/local: command not found
sunny@sunny-laptop:~$ patch -b<abc.patch
bash: abc.patch: No such file or directory
sunny@sunny-laptop:~$ ./install
bash: ./install: No such file or directory
sunny@sunny-laptop:~$ sudo In-s/home/sunny/programmer/ns-allinone-2.34/ns-2.34/ns/usr/bin/ns
[sudo] password for sunny: 
sudo: In-s/home/sunny/programmer/ns-allinone-2.34/ns-2.34/ns/usr/bin/ns: command not found

---

