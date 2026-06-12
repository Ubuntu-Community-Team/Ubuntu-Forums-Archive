---
title: "Internet connection"
date: 2009-01-15
forum: General Help
---

### Post by jan23778 on 2009-01-15
Hi everyone,

I am a very basic user of Ubuntu and have a problem that I cant work out. I created a user for myself with admin privileges and this works fine. Then I created a profile for my girlfriend (so that she would not keep cluttering up my desktop with thousands of files, icons and pictures) I also gave her administration privileges but when she logs in with her user name, she cannot get an internet connection, or for that matter can I if she logs in first. After a bit of experimentation I found out that if I logged in first and then she logs in after I do, both of us get a perfect connection. This defeats the purpose of having two users as if I am not there she would have to log in with my password and I would like to have a few pictures of women with skimpy clothing on my desktop but I don't think she would approve. (joke). 

Does anyone know why this is happening?

---

### Post by Macchi on 2009-01-15
Log in with your account with administrator privileges (at least the first user account that you have created) and try the following:

1) Go to the menu System->Administration->Users and Groups

2) Then klick "Unlock" and use your password.

3) Klick on your girlfriends user name and choose "Properties"

4) On the "User Privileges" tab you may allow her to connect to internet in different ways. Settings will be valid after she logs in again, but try a reboot of the whole system to see if she can connect. 

Please tell us if this works, otherwise we must try alternatives.




PS: By the way since you are already adjusting user privileges you could also remove her administrative rights on the system. (But never tell a feminist that you did that).

Limiting the number of people with administrative rights in the system will probably improve stability and security. I personally do not grant admin rights to everyone. Otherwise caos may grow and every setting may change all the time...

---

### Post by jan23778 on 2009-01-15
Hi Macchi,

Thank you very much for your reply.

I went to where you stated and there was a box "connect to wireless and ethernet networks" unticked, so I ticked this and was sure it was going to work but when I rebooted (just my girlfriends account) it still did not connect-

I am sorry to make you work hard at this but do you have any other suggestions?

By the way, I am a completely new user (you can probably tell) and it is my first experience with Linux and I am absolutely in love with it!! The cherry on the cake is all the support that you and all the other people on this site (and other sites) give new users, it makes it so much less daunting for any users that are a little worried about learning a new operating system. 

THANKS!!=D>

---

### Post by Macchi on 2009-01-15
Hi again jan23778,


Is your computer connected to the internet through a cable (often a desktop) or wireless network (often a laptop) or maybe a modem?
See below:

WIRELESS
If it is connected through a protected wireless network then you should attempt to log in with your girlfriends account and provide the key to the wireless net, so that the key is stored on her so called keychain.
(The reason for this limitation on sharing keys is that different users shall be able to use the same laptop on different networks with authentication on an individual level.)

CABLE
If you connect through a cable then this problem is quite uncommon.We will have to continue the diagnosis later.


MODEM 
If the computer is connected through an ADSL model or similar solutions then there are some other user privileges on modems, and connections that migth have to be adjusted.


Keep us informed on how it works (or not) and we will try again.



PS: I am glad that you have noticed that there is technical and human cooperation in the free software community in many different ways. The most direct form of cooperation is that the software itself is developed as a common project on a free will basis. 
After the software is released and starts to be used by a wider number of users then a different type of cooperation starts: technical support on the forums. 
Ubuntu happens to have a very good combination of software solutions, in a pretty and quite attractive package and surrounded by an active community. The at least three important success factors.

---

### Post by jan23778 on 2009-01-16
Hi Again Macchi,

My computer is connected through a protected wireless network. We have already tried to log in with my girlfriends account and provide the key to the wireless net. It still is not logging on when she logs into her profile first. It is a bit strange as we have absolutely no problems when I log in first and then she logs in after me.

I hope I am not starting to be a pain in the backside!

Thanks againg for your help and if there is anything else at all you could suggest I would really appreciate it.

---

### Post by jan23778 on 2009-01-16
Also in addition it doesn't log in even when the right key is inputted there and then.

---

### Post by Macchi on 2009-01-16
Hi Again,

We should keep trying untill the problem is solved. Communication of a forum requires some patience and is almost like playing chess through telegrams in the old days. 
Anyway, this problem must be related to privileges in the system.



Please test a few more things:

A) Double Check that all the necessary privileges on your girlfriend's user account are enabled.

B) Connect through a cable directly to the router and check that she has access to the internet after a reboot.  


C) Try also to erase your girlfriend's encrytion keys (related to wireless networks), reboot, and provide the keys again. Test if it works. PS: If possible do not erase all keys or she might loose other stored passwords. 

In order to do that login on her account, Go to Menu "Applications"->"Accessories"->"Password and Encryption Keys" then choose the tab "Passwords" and right-click on a key probably called "Network secret for xxx". Delete it, Quit, and reboot.
Then try to connect again to the wireless network. You will have to provide new keys.



I don't know if this works, in the meanwhile we can look for eventual bugs related to this area. One theory is that the existing keys on your girlfriend's account have been created when she actually had no privileges to connect. That can be a potential problem, thus it is good to try again with "fresh" keys.

PS: I am in GMT+1 time zone. Now it is friday evening amd thus I will be able to read you answers only tomorrow. Keep in touch.

---

### Post by mssever on 2009-01-16
The reason everything works if you log in first is because NetworkManager (which, not surprisingly, handles network connections) keeps the wireless connection active even if you log out. If Macci's suggestions don't get you anywhere, you might check whether her account can get on a different wireless network (at Starbucks, a hotel, etc.). Sometimes, wireless will decide it just doesn't like a particular network. You can also try changing the SSID of your network.

But try Macci's suggestions first, since they're more likely to work.

---

### Post by jan23778 on 2009-01-19
Thank Macchi and thanks MSSEVER.

I will try those suggestions and let you know how I get on. Sorry I was not able to get on during the weekend, I had a busy one!!

By the way I do have a wireless connection but it is not to a laptop, it is to a desktop PC so trying it on another network (like a public one at Starbucks or the library) would not really be possible.

Thanks again to both of you and I will let you know as soon as I have tried all the suggestions.

---

### Post by jan23778 on 2009-01-19
Hi again,

I still have had no joy even after following your advice:

A) I checked that the privileges on my girlfriends account were enabled and that was fine everything was ticked.

B) I connected via just a cable but could get no internet at all, it is an old cable and I have never tried to get a connection on this computer via cable so I cannot confirm if this has ever worked. I don't particularly want to go and buy a new cable just to test the connection if I can help it as money is tight at the moment! But let me know if it was absolutely necessary and I will see what I can do.

C) I erased my girlfriends keys and reinserted them to give it a fresh start but it still did not connect. I went into my password and encryption keys and I seem to have 2 "network secrets for Hooky (the name of the connection)" I did not want to delete them as I did not want to start fiddle as I seem to get into trouble when I start to do things from initiative but is there a reason that there are 2 that seem identical when my girlfriend only had 1? And could this sopmehow be related to the problem? If I should delete one would it be best to delete the top or the bottom one?

Thanks again for all your support

---

### Post by jan23778 on 2009-01-19
Hi Msserver,

You mentioned changing the SSID of the network, how do I do this and what other problems would I encounter if I logged on to this new network with other computers (I have a laptop I sometimes use with this same connection but prefer using the tabletop PC as it is more powerful)

Thanks

---

### Post by mssever on 2009-01-19
> **jan23778 said:**
> Hi Msserver,

You mentioned changing the SSID of the network, how do I do this and what other problems would I encounter if I logged on to this new network with other computers (I have a laptop I sometimes use with this same connection but prefer using the tabletop PC as it is more powerful)

Thanks
To change the SSID, you have to go to your router's configuration tool. Usually, that means pointing a web browser at the router's IP address. If you change the SSID, other computers won't be able to connect until you re-enter the keys. Once you enter the key, though, everything should be fine.

---

