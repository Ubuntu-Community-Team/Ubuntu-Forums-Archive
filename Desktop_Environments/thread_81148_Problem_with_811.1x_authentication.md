---
title: "Problem with 811.1x authentication"
date: 2005-10-23
forum: Desktop Environments
---

### Post by quiteNewbee on 2005-10-23
Hi

I've spent the last hours trying to get xsupplicant to work on my computer. I am trying to access my university account to the internet.

Finally I think I've gotten things quite close to work, but I get this message when I try to run xsupplicant:

sentinel@sentinel:~$ sudo xsupplicant -i eth0 -c /home/sentinel/xsupplicantmini.conf -f
Error in (null), at line 8:
syntax error:

startup_command = <BEGIN_COMMAND>ifconfig eth0 allmulti 0.0.0.0 up<END_COMMAND>
                                               ^ (the marker is under the = sign, but the formatting gets screwed up here)

                
General Parse error!
There was a problem with the config file.  We cannot continue.
sentinel@sentinel:~$

Here is my .conf file. Its a miniversion of the original one, just with the options needed to access our network:

### GLOBAL SECTION

network_list = all
default_netname = default

startup_command = <BEGIN_COMMAND>ifconfig eth0 allmulti 0.0.0.0 up<END_COMMAND>
first_auth_command = <BEGIN_COMMAND>dhcpcd -n<END_COMMAND>
reauth_command = <BEGIN_COMMAND>dhcpcd -n<END_COMMAND>

logfile = /var/log/xsupplicant.log

deny_interfaces = lo

###  NETWORK SECTION

default
{

  type = wired
  allow_types = all
  identity = <BEGIN_ID>(my mail)<END_ID>

  eap-peap {
      root_cert = /etc/1x/cert/demoCA/cacert.pem
      root_dir = /etc/1x/cert/demoCA
      chunk_size = 1398
      random_file = /etc/1x/cert/random
      session_resume = yes
      allow_types = all # where all = MSCHAPv2, MD5, OTP, GTC, SIM

      eap-mschapv2 {
        username = <BEGIN_UNAME>(my username)<END_UNAME>
        password = <BEGIN_PASS> (my passwd)<END_PASS>
      }
  }
}


I don't understand why it stops there... Anyone who knows why?

/fluX

---

### Post by theantidj on 2005-11-06
One of the problems with Xsupplicant is that their documentation is horribly out of date.  I'm also trying to get it to work. 

What version are you running?  One thing I've learned is that in the recent versions is that you no longer need to use the <begin command> type tags.  Remove all of the < > tags from your config file, just set the value you want and see if that works.


Good luck.

---

