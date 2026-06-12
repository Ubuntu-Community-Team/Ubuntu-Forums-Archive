---
title: "some websites don't work"
date: 2005-01-11
forum: Desktop Environments
---

### Post by doni on 2005-01-11
hi there...

i'm having the strange problem, that some website (for example ubuntuforums) don't work in ubuntu, some others (google, osnews, deviantart, ...) work. 
they do work in windows, but not in ubuntu...

what could be the problem? can't be a firewall issue (i couldn't also remember that i've installed one), because it can't block port 80 whitout blocking all websites....!?

thanks for help!
doni

---

### Post by hardcandy on 2005-01-11
It seems it  is a rendering issue. Have you changed anything just prior to this happening? Any updates? Any new software? Any changes to Firefox? Also, did you install adblocker in Firefox and block any ads?

---

### Post by doni on 2005-01-11
no it says "can't connect to www.osnews.com" or something...

---

### Post by hardcandy on 2005-01-11
I hate to say this in a linux forum maybe try rebooting and see what happens? Maybe the /etc/resolv.conf got messed up? Or the nameservers your ISP uses are having a hiccup?

Did you change any network settings? Disable any IpV stuff?

---

### Post by doni on 2005-01-12
reboot didn't fix it...

i didn't change any network settings, but i tried to deactivate my netword card and reactivated it, but it didn't fix it too....

i'll have a look at my resolv.conf this evening! thanks for help

---

### Post by nocturn on 2005-01-12
[QUOTE=doni]reboot didn't fix it...

i didn't change any network settings, but i tried to deactivate my netword card and reactivated it, but it didn't fix it too....

i'll have a look at my resolv.conf this evening! thanks for help[/QUOTE]

Try in a terminal for the sites that do not work:
host [www.site.domain](www.site.domain)
ping [www.site.domain](www.site.domain)

Have you configured the proxy in FireFox correctly?

---

### Post by doni on 2005-01-12
no it can't be a firefox problem. i can't get my mail in thunderbird, too (host not found), no problem under windows....

i'm sure there aren't any broken settings in firefox / thunderbird, because it did work a day ago, and i didn't change anything. trust me :-)

---

### Post by ra1 on 2005-01-12
It's probably a dns problem. Take a look at your /etc/resolv.conf.
   And try what nocturn suggested [QUOTE=nocturn]Try in a terminal for the sites that do not work:
    host [www.site.domain]("http://www.site.domain/")
    ping [www.site.domain]("http://www.site.domain/")
    [/QUOTE]

---

### Post by nocturn on 2005-01-12
[QUOTE=doni]no it can't be a firefox problem. i can't get my mail in thunderbird, too (host not found), no problem under windows....

i'm sure there aren't any broken settings in firefox / thunderbird, because it did work a day ago, and i didn't change anything. trust me :-)[/QUOTE]


Another question.
How are you connecting to the Internet?

Do you have a router/firewall at home?  
Are you hooked up to an ISP directly?
Are both Windows and Linux set to use DHCP?

---

### Post by doni on 2005-01-12
i'm conntected with ADSL, my router is a zyxel hw 650 and both windows and linux are conntected with the same cable on the same router with the same dhcp :)

thanks

---

### Post by nocturn on 2005-01-12
[QUOTE=doni]i'm conntected with ADSL, my router is a zyxel hw 650 and both windows and linux are conntected with the same cable on the same router with the same dhcp :)

thanks[/QUOTE]


You are sure that your ubuntu box is configured to user DHCP?

If so,  check the files in /var/log for dhcp entries.

In a terminal:
grep -H -i "dhcp" /var/log/*

Will do the trick.

---

### Post by python on 2005-01-17
Got to be bloody DNS!



Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}


That should have you sorted sunshine!

---

