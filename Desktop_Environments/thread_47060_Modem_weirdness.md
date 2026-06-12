---
title: "Modem weirdness"
date: 2005-07-07
forum: Desktop Environments
---

### Post by spedsta on 2005-07-07
Hi i have a external modem , and configured it using the dialer in System --> Networking. 

Ok here is the real weird thing, it finds the modem on the right port, I activate it and it starts dialing, then it makes the connect sound(bing ) and then continues with the sort of static sound again (shhhhhhhh).This continues as long as I got the connection active. I read somehere else thats it could be going into a loop.
So i thought maybe it was an authentication thing, maybe the authentication settings was not configured correctly but guess what,  I try firefox and I can actually start surfing the web, allbeit very slow!!
Much slower than i did on windows and Mandrake ( my previous distro), which worked the day before.

I tried evolution and it worked flawlessly. except it was just slow 
I then tried dialing up in winxp and it worked fine.Switched back to Ubuntu and the same thing?

I don't know what the problem is here -->  thats why i post it in here, my best guess is that its a configuration problem but who knows , do you?

besides this dialup hiccup, so Far its all good
I would really appreciate it if you could help, 
thanks

---

### Post by spedsta on 2005-07-08
I found WVdial tuts and used that but something else is happening now, its starting up like it should and then terminating imeddiately. Here is the print out from the terminal using Wvdial.:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK
--> Modem initialized.
--> Sending: ATDT0214068500
--> Waiting for carrier.
ATDT0214068500
CONNECT 52000/ARQ/V90/LAPM/V42BIS
CChecking authorization, Please wait...
username:
--> Carrier detected.  Waiting for prompt.
username:
--> Looks like a login prompt.
--> Sending: [email]wells@discoverymail.co.za[/email]
[email]wells@discoverymail.co.za[/email]
password:
--> Looks like a password prompt.
--> Sending: (password)
cas5-ctn>
--> Hmm... a prompt.  Sending "ppp".
ppp
Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP address is 0.0.0.0. MTU is 1500 bytes
--> Looks like a welcome message.
--> Starting pppd at Fri Jul  8 00:40:45 2005
--> pid of pppd: 7472
--> Disconnecting at Fri Jul  8 00:40:46 2005
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


 I hope someone can help me cause i need my internet connection for more than just installing new software. besides ubuntu is really empty without a connection. might have to consider another distro which will allow me to dialup, don't wanna but have to go with what works --right? :?

---

### Post by spedsta on 2005-07-08
OK in a bid to get someone to post a solution , i have done some digging online and saw that maybe i should try using pppconfig, so maybe thats a solution , any other ideads out there?

another problem i have after tbgetting myself online is that i have saved my old evoution folders(mandrake) from my home folder. I thought that maybe i can pop that into my new home folders and voila evolution will get all my mail , etc.
when starting up evolution it complained about merging mail and crashed , i moved the folders(evoution & .evolution) and it started normally again but with nothing in it.
 i know my mail is in there somewhere cause its big , too big for just some config files!

I hope you guys can help as I am really desperate here   :roll: 

thanks ahead of time

---

