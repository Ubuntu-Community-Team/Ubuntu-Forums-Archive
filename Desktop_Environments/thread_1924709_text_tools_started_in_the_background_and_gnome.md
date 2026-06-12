---
title: "text tools started in the background and gnome"
date: 2012-02-13
forum: Desktop Environments
---

### Post by centek1 on 2012-02-13
Hi,
I have a vpn client which is old school text application - just asks for credentials, makes vpn connection and goes to the background.
Another tool has to be executed (simple sh script) to stop the vpn app - the script just looks for the vpn app pid
and kills it...

Everything works as expected, dont have issues to that... but yesterday I decided to put a shortcut to it on gnome desktop...

I want to have such behaviour:

1. click on vpn shortcut on desctop
2. vpn app starts, it asks for credentials in normal way, in text terminal 
3. once correctly provided credentials goes to background, text terminal is closed - I am vpn connected
4. automatically there should be an icon added to system tray area, which i can double click to disconnect the vpn

how to do that? Would preffer not fancy low level programming in ASM or C... 

I think everybody understand what is the need but 
to be more descriptive:

i assume I should do a some kind of script started when clicked on the desctop vpn shortcut i prepared - 
which in pseudo-code should look like this:

00 #LAUNCH_VPN:
01 start_vpn_script # goes to the background fi ok, or exit 1 if fail
02 if ret == 0 then create systray icon /shortcut to the stop_vpn_script

when i click the systray icon/shortcut - the stop_Vpn_script is started and actually kills the start_vpn_script background job, and exits...

note - both start_vpn and stop_vpn scripts are available... 

hope somebody has smart solution...

---

