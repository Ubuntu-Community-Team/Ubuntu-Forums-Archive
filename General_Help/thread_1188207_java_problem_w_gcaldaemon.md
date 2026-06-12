---
title: "java problem w gcaldaemon"
date: 2009-06-15
forum: General Help
---

### Post by adelattre on 2009-06-15
I'm trying to install and run gcaldaemon.  I'm having trouble getting the program to find java.  I've gotten help finding the path to java, and making it work once [detailed below], but I can't seem to make the path to java permanent, so each time I restart, or even after I've started gcaldaemon [standalone-start.sh] it loses the path to java and I get an error.

I knew that there was a problem early on because one of the first instructions for installing gcaldaemon is to confirm java.  When I typed "java -version" and it returns:

andre@andre-laptop:~$ java -version
The program 'java' can be found in the following packages:
* gij-4.3
* java-gcj-compat-headless
* openjdk-6-jre-headless
* cacao
* gij-4.2
* jamvm
* kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
andre@andre-laptop:~$ 

I had installed sun-java6-bin, -jre, and -plugin via synaptic. 

Next, I confirmed that package "sun-java6-bin" properly installed:
Code:
dpkg -l sun-java6-bin
which shows
Code:
andre@andre-laptop:~$ dpkg -l sun-java6-bin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii sun-java6-bin 6-13-1 Sun Java(TM) Runtime Environment (JRE) 6 (ar
andre@andre-laptop:~$ 

Then, to find the file "java" in the bin directory:
Code:
andre@andre-laptop:~$ dpkg -L sun-java6-bin |grep bin/java$

/usr/lib/jvm/java-6-sun-1.6.0.13/jre/bin/java

/usr/lib/jvm/java-6-sun-1.6.0.13/bin/java

andre@andre-laptop:~$ 


Then, to set the PATH I ran:
Code:
andre@andre-laptop:~$ /usr/lib/jvm/java-6-sun-1.6.0.13/bin/java -version

java version "1.6.0_13"

Java(TM) SE Runtime Environment (build 1.6.0_13-b03)

Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)

andre@andre-laptop:~$ export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.13/bin



At which point, the command “java -version” works, returning:

Code:
andre@andre-laptop:~$ java -version

java version "1.6.0_13"

Java(TM) SE Runtime Environment (build 1.6.0_13-b03)

Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)

andre@andre-laptop:~$ 


And at this point I could run the gcaldaemon pieces that I was trying to do in the installation and set-up [so, first running “password-encoder.sh”, and later “standalone-start.sh”], but they only run once, and then I can't even get 'java -version' to return anything other than the original error that I got at the top, and when running the standalone-startup.sh it gets started, but then when it trys to execute one of the commands it gets a java error

so, running “standalone-start.sh” returns:

Code:
andre@andre-laptop:/usr/local/sbin/GCALDaemon/bin$ ./standalone-start.sh

INFO  | GCALDaemon V1.0 beta 16 starting...

INFO  | RSS/ATOM feed converter enabled.

INFO  | Local time zone is Central Standard Time.

INFO  | HTTP server starting on port 9090...

WARN  | Set the 'http.allowed.hostnames' parameter to limit remote access.

INFO  | HTTP server started successfully.

INFO  | Start listening file /usr/local/sbin/GCALDaemon/google.ics...

INFO  | File listener started successfully.

INFO  | Offline file synchronization enabled.

INFO  | LDAP server disabled.

INFO  | Gmail notifier disabled.

INFO  | Sendmail service disabled.

INFO  | Mail terminal disabled.

WARN  | Received file from Google:

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"><html><head><meta http-equiv="content-type" content="text/html;charset=utf-8">

<title>Calendar Error</title>

<style type="text/css">

body,td,div,.p,a,font,span {font-family: arial,sans-serif}

.bubble {background-color:#C3D9FF}

.tl {background-image: url(/calendar/images/corner_tl_gmail.gif);

background-position:top left;background-repeat:no-repeat}

.tr {background-image: url(/calendar/images/corner_tr_gmail.gif);

background-position:top right;background-repeat:no-repeat}

.bl {background-image: url(/calendar/images/corner_bl_gmail.gif);

background-position:bottom left;background-repeat:no-repeat}

.br {background-image: url(/calendar/images/corner_br_gmail.gif);

background-position:bottom right}

.tl, .tr, .bl, .br {background-repeat:no-repeat}

</style></head>

<body bgcolor="#ffffff" style="margin-top:2px; "><table width="95%" border="0" align="center" cellpadding="0" cellspacing="0"><tr valign="top"><td width="1%"><a href="http://www.google.com/calendar"><img border="0" width="143" height="59" align="left" vspace="10" alt="Google Calendar" src="/calendar/images/calendar_sm2_en.gif"></a></td>

<td width="99%" bgcolor="#ffffff" valign="top"><table width="100%" cellpadding="1"><tr valign="bottom"><td><div align="right">&nbsp;</div></td></tr>

<tr><td nowrap><table width="100%" align="center" cellpadding="0" cellspacing="0" style="margin-bottom:5px;background:#C3D9FF"><tr><td class="bubble tl" width="4"></td>

<td class="bubble" rowspan="2" style="font-family:arial;text-align:left;font-weight:bold;padding:3px,0px;"><b>Calendar Error</b></td>

<td class="bubble tr" width="4"></td></tr>

<tr><td class="bubble bl" width="4"></td>

<td class="bubble br" width="4"></td></tr></table></td></tr></table></td></tr></table>

<br>

<table width="94%" border="0" align="center" cellpadding="5" cellspacing="0"><tr valign="top"><td>Calendar Error</td></tr>

</table>

<br><br>

<table width="95%" align="center" cellpadding="3" cellspacing="0" style="margin-bottom:5px;background:#C3D9FF"><tr><td class="bubble tl" width="4"></td>

<td class="bubble" rowspan="2" style="font-family:arial;text-align:center;"><font size="-1" color="#666">&copy;2009

Google -

<a href="http://www.google.com">Google Home</a></font></td>

<td class="bubble tr" width="4"></td></tr>

<tr><td class="bubble bl" width="4"></td>

<td class="bubble br" width="4"></td></tr></table></body></html>





So, this is where I'm stuck.  My guess is that I've failed to do something that allows gcaldaemon to find java permanently, but I'm not sure.

Advice?  Other info that would be needed to diagnose my situation?
Thanks.

---

### Post by adelattre on 2009-06-15
OK, so a post on another board helped me solve the problem of making the PATH to java 'permanent' - the advice was:

So all you will need to do is add the following line anywhere in that file using your favorite text editor, and save it. To test it, open up a new terminal and run 'java -version', and see if the output is as you expect. 
 
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.13/bin 
 
So your file might look like this... 
 
# my favorite aliases 
alias rm='rm -i' 
alias cp='cp -i' 
alias mv='mv -i' 
 
#export path for gcaldaemon 
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.13/bin 
 
Make sense? You can use .bashrc for all sorts of other things too: command aliases, setting colors, tab-completion, and more.

---

### Post by nolliecrooked on 2009-06-15
did you try installing the latest 1.6.0.14 java from;

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

?

---

