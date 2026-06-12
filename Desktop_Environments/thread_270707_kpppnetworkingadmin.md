---
title: "kppp/networking/admin"
date: 2006-10-03
forum: Desktop Environments
---

### Post by the.phantom on 2006-10-03
ok i will admit i am probably the last person with just dialup !


i can get the dialup to work just fine with system/administration/networking
but i have a problem i found out on linspire a while ago

i need to set the transfer rate of the serial port
so i found the solution was KPPP
i could run it as admin as that was a default screen
if i tried to run it as user i could not get it to work and someone had a linspire fix that was a kludge but worked

so in the ubuntu networking i have only dial number and username/password i can change

in kppp i can controll the serial port/modem speed and with a 56k modem 57k works just fine


so i installed kppp
configured it , but would not log in to the isp
would connect but not log in

so i tried "sudro kppp"  ( without quotes)in the terminal screen
(that was tried when i was with linspire and didn't work either)
and screen scrolled and could not find a few things, then i got my kppp gui 

but just like linspire a error and would not work

i need to have the seral  port set for 5700 only and stay at that with networking
or get kppp to work


i have buffer troubles and can't send a e-mail longer than say 5 k or it just hangs and never sends it 

i am a lightweight with linux so details on any answer would be appreciated or a work around?

i don't know how to try and get in and edit somewhere a file for speed on a  serial port

---

### Post by the.phantom on 2006-10-13
well i did a search and found a bunch of kppp troubles 
and then learned how to "gksudo nautilus"
and got rid of the # in 
ect/ppp/peers/kppp-options
then i could login and send a attachment as the default dialer is weak and will not allow you to change the serial port speed so my buffer was over run !

so anyone who reads this for help this might help?

just do a alt f2 and type gksudo nautilus and you will be in root so you can edit a file as you will need root permission to do it

---

