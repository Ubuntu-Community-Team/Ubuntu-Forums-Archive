---
title: "No graphic interfce from SSH"
date: 2010-10-18
forum: Desktop Environments
---

### Post by runningpig001 on 2010-10-18
Hello, all

I am having an annoying problem with ubuntu 10.04.
with SSH, I get connected to a linux server. The command line works well.
But I can NOT get a graphic interface from it.
For example:

###############################################################
[COLOR="Red"]me@power:~$ ssh -Y me@123.456.789.3[/COLOR]
me@123.456.789.3's password: 

[COLOR="Red"][me@master]#gedit abc.f[/COLOR]

(gedit:23385): Gtk-WARNING **: cannot open display:  

[COLOR="Red"][me@master]#matlab[/COLOR]
Warning: Unable to open display '123.456.789.223:0.0'.  You will not be able to display graphics on the screen.

                              < M A T L A B >
                  Copyright 1984-2007 The MathWorks, Inc.
                         Version 7.5.0.338 (R2007b)
                               August 9, 2007

Warning: Name is nonexistent or not a directory:
/usr/local/matlab/toolbox/readgrib.
 
  To get started, type one of these: helpwin, helpdesk, or demo.
  For product information, visit [www.mathworks.com](www.mathworks.com).

#######################################################################
where 123.456.789.3 is the server's ip and 123.456.789.223 is my ip.

According to some ppl's suggestion, I have changed my ~/.ssh/config file to 

############
GSSAPIAuthentication no
ForwardX11 yes
############

but it does not help.

The OS I am working with is ubuntu 10.04
the GNOME version is 2.30.2

So any suggestion please?
Thank you!

&#65339;SOLUTION&#65341;just comment one line in the .cshrc file in my home folder in the server
#setenv DISPLAY 123.456.789.223:0.0

it's said this line is not needed for linux system trying to connet to the server.

---

### Post by tisungho on 2010-10-18
should it be ssh -X ...?

---

### Post by runningpig001 on 2010-10-18
> **tisungho said:**
> should it be ssh -X ...?

I tried it too, it did not work either.

---

### Post by tisungho on 2010-10-18
Does your linux server have X server running?

---

### Post by runningpig001 on 2010-10-18
> **tisungho said:**
> Does your linux server have X server running?

I have solved the problem    thank you all the same

---

