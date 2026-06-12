---
title: "can not open websites"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by uppsluppen on 2009-03-22
Dear all.
I am new to this and annoyance with windows drove me to ubuntu, but what I now experience is even worse.
I have a Dell netbook mini with "ubuntu 8.04 the hardy heron".
Neither with Firefox nor with Epithany can I open websites.
I can access the web with the search engine but I can open only very few sites. When checking the error console in firefox I sometimes get following message:"error in parsing value for property..."
This means nothing to me.
I checked some of the threads on this forum and I came accross some similar problems, but I still could not solve mine.
I hope to find some help here, thanks.

---

### Post by ugm6hr on 2009-03-22
Not heard of this before.

Perhaps some detail might help?

Let us know what which websites are the problem.

And are you able to ping those websites from Terminal (example below)?

```
ping -c 3 www.google.com
```

How do you get online?  E.g. wifi router etc.

---

### Post by uppsluppen on 2009-03-22
I can get into google and search, works very well.
But I can not open any of the results, especially newspapers or I can access Youtube, but can not download any of the clips. I can access some websites but only if there are no pictures in there. I would say 90% of sites I tried failed me.
I connect wifi. Sorry to sound quite a bore but I do not even know how to ping from terminal.:(

---

### Post by ugm6hr on 2009-03-22
> **uppsluppen said:**
> I connect wifi. Sorry to sound quite a bore but I do not even know how to ping from terminal.:(

I gave an example in the last post.

See the Code in Terminal link below.

And some specific website examples please.

---

### Post by uppsluppen on 2009-03-22
I just tried to ping and get 7 lines of strange text:
ping [www.google.com(209.85.229.108](www.google.com(209.85.229.108)) 56(84) bytes of data.
64 bytes from [www.l.google.com](www.l.google.com) (209.85.229.104):icm_seq=1 ttl=243 time=32.9ms.
Three more lines of almost the same and then:
3 packets transmitted, 3 received, 0% packet loss, time 2001ms rtt min/avg/max/mdev=32.064/32.594/32.977/0.414 ms.

This site I can not open, [http://www.guardian.co.uk/](http://www.guardian.co.uk/)
This is one of the very few I can open, [http://www.coarsefish.org/](http://www.coarsefish.org/)

---

### Post by ugm6hr on 2009-03-22
So you can resolve google.

Try guardian:
```
ping -c 3 www.guardian.co.uk
ping -c 3 212.187.153.30
```

Just need to know whether the results are as before, or if it gives an "unknown host" error.

---

### Post by uppsluppen on 2009-03-22
When I ping the guardian. I get:
3 packets transmitted, 3received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev=46.481/52.051/55.330/3.959 ms

---

### Post by uppsluppen on 2009-03-22
nope, it does not give an unknown host error.

---

### Post by ugm6hr on 2009-03-22
OK.

So you can resolve DNS from Terminal.

Hmmm....

Try these links in Firefox now:
[http://212.187.153.30/](http://212.187.153.30/)
[http://www.guardian.co.uk/](http://www.guardian.co.uk/)

---

### Post by uppsluppen on 2009-03-22
neither of the two work. Firefox tries for ever to load but to no avail.

---

### Post by ugm6hr on 2009-03-22
This may be because of some corruption in your FF profile, or its cache.  Doesn't really explain why Epiphany does the same.

Go to Tools -> Clear Private Data, tick everything for deletion, and then close and restart FF.

Then try those links again.

Have you added any FF Add-ons?

The other thing to try is deleting your profile (will lose all bookmarks and everything):

Close FF.
Go to Terminal (in Applications -> Accessories)
```
rm -rf ~/.mozilla
```

Then restart FF and try again.

Just to clarify - this is a problem with FF rather than Ubuntu, since Ubunu itself can access the websites.

There is one other possibility - ipv6.  However, the guardian website is not an ipv6 offender (since I can access it in my Mini browser).

---

### Post by uppsluppen on 2009-03-22
no, I added no add ons.
It is not just the guardian, which does not load, but almost no other websites either.
I followed your instructions and deleted all private data and also my profile as you suggested and the result is not any better than before. 
Could the reason for my troubles be somewhere with java?

---

### Post by alicemoon on 2009-03-22
I had a similar problem - have a look at the thread [http://ubuntuforums.org/showthread.php?t=837413](http://ubuntuforums.org/showthread.php?t=837413)
and eventualy discovered that ubuntu did not recognise the MTU setting in my router - it was easy to fix by adding a line in the /etc/network/interfaces file - check out the end of my thread for instructions on how to do it.

---

### Post by linuxrollup on 2009-03-22
Go on to Edit --> Preferences --> Advanced --> Network and under connection, select settings and select the no proxy option. See if that works.

---

### Post by uppsluppen on 2009-03-23
> **linuxrollup said:**
> Go on to Edit --> Preferences --> Advanced --> Network and under connection, select settings and select the no proxy option. See if that works.
Do you mean the Network Proxy Preferences?
I checked those and they were set at Direct internet connection.
Manual proxy and automatic proxy are off.

---

### Post by brianchidester on 2009-03-23
Are you using the regular 8.04 desktop or the customized Dell 8.04 (with Dell launcher)?

---

### Post by uppsluppen on 2009-03-23
> **brianchidester said:**
> Are you using the regular 8.04 desktop or the customized Dell 8.04 (with Dell launcher)?
it is the regular

---

### Post by uppsluppen on 2009-03-23
> **alicemoon said:**
> I had a similar problem - have a look at the thread [http://ubuntuforums.org/showthread.php?t=837413](http://ubuntuforums.org/showthread.php?t=837413)
and eventualy discovered that ubuntu did not recognise the MTU setting in my router - it was easy to fix by adding a line in the /etc/network/interfaces file - check out the end of my thread for instructions on how to do it.
I followed the thread. It sounded all very promising, but although I have a Belkin router we could not find a MTU.

---

### Post by alicemoon on 2009-03-23
> **uppsluppen said:**
> I followed the thread. It sounded all very promising, but although I have a Belkin router we could not find a MTU.
 ok here's how you do it on my router - hopefuly yours is similar
put 192.198.2.1 into firefox bar
this should get you into the router setup
there is a menu on the left click on Internet Wan > Connection type
you may have to enter a password if there is one set
then click thropugh till you get to the  PPPoA Interface page where one of the settings is MTU 

hope this helps - let me know if it works

---

### Post by uppsluppen on 2009-03-23
> **alicemoon said:**
> ok here's how you do it on my router - hopefuly yours is similar
put 192.198.2.1 into firefox bar
this should get you into the router setup
there is a menu on the left click on Internet Wan > Connection type
you may have to enter a password if there is one set
then click thropugh till you get to the  PPPoA Interface page where one of the settings is MTU 

hope this helps - let me know if it works
 Thanks, I found it at last.
My MTU is set at 1492. What shall I change it to if at all?

---

### Post by alicemoon on 2009-03-23
mine was 1432 I then edited the /etc/network/interfaces file  using sudo gedit and beneath the lines
auto eth0
iface ehth0 inet dhcp
added the line
pre-up /sbin/ifconfig $IFACE mtu 1432
and then saved the file
however if yours is already 1492 you could try adding
pre-up /sbin/ifconfig $IFACE mtu 1492 to the file first before changing the MTU in the router
Don't forget to save an original copy of your interface file incase things go wrong

---

### Post by uppsluppen on 2009-03-23
> **alicemoon said:**
> mine was 1432 I then edited the /etc/network/interfaces file  using sudo gedit and beneath the lines
auto eth0
iface ehth0 inet dhcp
added the line
pre-up /sbin/ifconfig $IFACE mtu 1432
and then saved the file
however if yours is already 1492 you could try adding
pre-up /sbin/ifconfig $IFACE mtu 1492 to the file first before changing the MTU in the router
Don't forget to save an original copy of your interface file incase things go wrong
sorry, how and where do I enter the sudo gedit?

---

### Post by uppsluppen on 2009-03-23
> **alicemoon said:**
> mine was 1432 I then edited the /etc/network/interfaces file  using sudo gedit and beneath the lines
auto eth0
iface ehth0 inet dhcp
added the line
pre-up /sbin/ifconfig $IFACE mtu 1432
and then saved the file
however if yours is already 1492 you could try adding
pre-up /sbin/ifconfig $IFACE mtu 1492 to the file first before changing the MTU in the router
Don't forget to save an original copy of your interface file incase things go wrong
I guess I had to enter that in the terminal. I did so and got:
"bash: pre.up: command not found."
Does

---

### Post by alicemoon on 2009-03-23
ok - when you do things through terminal first always ensure you write the command in exactly or it will not be recognised  - it is usually you missing a digit or character if it fails to work.
secondly always save an original copy of the file you are changing
type into terminal exactly as follows with the same characters and spacing - paste in the line if need be (you can only do this in the terminal by using the drop down edit menu as shortcuts will not work
sudo gedit /etc/network/interfaces
then press enter - it will ask you for your password - write in your password (no letters or numbers will show but when you have finished press enter) and hopefuly if everything is correct it will open the /etc/network/interfaces file.
save a copy of this file call it interfacescopy1 or something incase you need it. Then reopen the original file and add in the line 
pre-up /sbin/ifconfig $IFACE mtu 1492 
as I suggested and save the file 
reboot your computer and see if it worked.

---

### Post by uppsluppen on 2009-03-23
> **alicemoon said:**
> ok -

. Then reopen the original file and add in the line 
pre-up /sbin/ifconfig $IFACE mtu 1492 
as I suggested and save the file 
reboot your computer and see if it worked.
mine was saying pre-up /sbin/ ifconfig $IFACE mtu 1432.
I just put the line, that you suggested below that. Or should I have replaced the initial line with yours?
However it now works even worse than before.

---

### Post by alicemoon on 2009-03-24
then I would suggest that you change the MTU in your router to 1432 so it matches

---

### Post by alicemoon on 2009-03-24
> **uppsluppen said:**
> mine was saying pre-up /sbin/ ifconfig $IFACE mtu 1432.
I just put the line, that you suggested below that. Or should I have replaced the initial line with yours?
However it now works even worse than before.

sorry just realised what you said - and apologies if I have not been clear

if it already has the line 
pre-up /sbin/ifconfig $IFACE mtu 1432
set the mtu in your router to match ie  1432
do not add in the line
pre-up /sbin/ifconfig $IFACE mtu 1492
as this will cause conflict 

if it does not work with the line
pre-up /sbin/ifconfig $IFACE mtu 1432
and the router setting is at 1432
then just change the end of that line to 1492
and change the router mtu setting back to 1492

make sure you get the line exactly right with spaces as I have written

don't forget to save and then reboot your computer after making changes to the /etc/network/interfaces file

---

### Post by uppsluppen on 2009-03-24
Dear Alicemoon,
it still does not work. I tried both options outlined by you and took great pains to do it correctly.
What I fail completely to understand is, why I can do my Google searches and open a very few websites, but the great majority of websites never load. Could the issue be one nothing to do at all with connection but with some of my software?

---

### Post by ugm6hr on 2009-03-24
> **uppsluppen said:**
> Could the issue be one nothing to do at all with connection but with some of my software?

This is what I believe.

More important than the fact that some websites work, and others do not, is the fact that you are able to ping a website by either its IP address or its url and connect to it.  However, that *same* website apparently does not load in either FF or Epiphany.

I am still unclear as to how this could happen.

To complicate things further, those websites you describe are perfectly compatible with the default Dell Mini Ubuntu (I have one, and can see the guardian site with no problems).

---

### Post by uppsluppen on 2009-03-24
> **ugm6hr said:**
> 

To complicate things further, those websites you describe are perfectly compatible with the default Dell Mini Ubuntu (I have one, and can see the guardian site with no problems).
Yes, and of course I tried out a great many other websites, not just the Guardian.
To which component of the software do my problems point?
Should it not be possible to remedy my problems by reinstalling the programmes which I got on CD? It should be feasible with an external cd drive?!

---

### Post by alicemoon on 2009-03-24
> **uppsluppen said:**
> Dear Alicemoon,
it still does not work. I tried both options outlined by you and took great pains to do it correctly.
What I fail completely to understand is, why I can do my Google searches and open a very few websites, but the great majority of websites never load. Could the issue be one nothing to do at all with connection but with some of my software?

looks like it is not the same problem I had although the symptoms are very similar. I could get into google, search on google and open a few websites but not the majority - - I know how frustrated you must feel! I don't think I can suggest anything else as I really don't know why changing the MTU settings solved my problem. I hope someone with more knowledge can help you and don't give up on Ubuntu as once it is running correctly it is excellent.

---

### Post by uppsluppen on 2009-03-24
> **alicemoon said:**
> looks like it is not the same problem I had although the symptoms are very similar. I could get into google, search on google and open a few websites but not the majority - - I know how frustrated you must feel! I don't think I can suggest anything else as I really don't know why changing the MTU settings solved my problem. I hope someone with more knowledge can help you and don't give up on Ubuntu as once it is running correctly it is excellent.
Dear Alicemoon,
thank you very much for your effort and patience in trying to talk me around solving my problem.

---

### Post by dagoth_pie on 2009-03-24
This is a little out of my area of knowledge, but as far as I know, both Firefox and Epiphany run over top of Gecko, maybe the problem is there, google is a fairly simple web page, and whatever part of Gecko could be missing might not be needed, you said with most web sites it comes up with a "parsing error"? that means, I assume (basing this on xml not html) that it didn't understand a tag somewhere, probably a fairly standard tag but one google doesnt use, any more suggestions anyone?

---

### Post by ferdinandfly on 2009-04-06
i have the same probleme. In addition, i can ping almost all the site but i can not do wget for most of them.
i check all the configuration and they are just as what you have told. 

it is very intresting that google works well but not yahoo, or unbutu, i can update my ubuntu but not the update list.

---

### Post by armandh on 2009-04-06
county GIS sites seem to open with windows but not linux
ff or ie does not matter

[http://www.lincolncomogis.com/lincoln/](http://www.lincolncomogis.com/lincoln/)
this opens in about 10 seconds with XP&IEorFF

says transfering data but never opens with 8.10&FF

---

