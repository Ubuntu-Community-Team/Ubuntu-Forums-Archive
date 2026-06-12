---
title: "email"
date: 2009-06-25
forum: General Help
---

### Post by mark.giblin on 2009-06-25
I asked this question for help a few months ago.

I have confronted the web host, tackled the ISP which cost me a £15 phone call just to confirm that the outgoing (sendingmail) issue on my PC is in fact the problem of LINUX.

Now is their ANYONE who can advise on why I can not get an outgoing smtp connection to the mailservers at the web host when I can colledt emails on the one and single URL that is used for sending and recieving emails.

If the issue was at the host server then I would not be able to collect emails at all but I can.

The issue FOR EVERYONE INFO is nothing to do with my PC, the HOST who BTW does not give email services and do not block any port, hence the 3rd party host as well as that theirs no issues with the host.

I have now spent nearly £50 on advise and troubleshooting this issue because help is not forthcoming, this is money that I can not afford to spend seeing as I am currently unemployed and do need to be able to send speculative emails and respond to online agencies.

what I can not wrap my head around is why ubuntu linux ships a diatro that is ready to collect emails but does not allow sending... Chocolate Tea pots in the desert spring to mind.

I really would like this sorted out as it has been months and not much in the way of help.

Thx.

---

### Post by ACupOfCoffee on 2009-06-25
What email client? What settings? Who's your provider? Getting any error messages?

I send and receive emails all the time from my Ubuntu machine so, you know, it CAN properly do email.

---

### Post by Subban on 2009-06-25
Of course linux can "do email", wanna bet that linux runs the majority of the worlds email ?

Provided you have configured your PC and router correctly which will be no doubt established shortly, I would warn against being absolutly cock sure that your ISP isn't blocking port 25 as it is fairly standard for them to do so as an anti spam measure in my experience. I have previously been told point blank by an ISP tech support they do not block outgoing port 25, to only find that they certainly did.

---

### Post by dcstar on 2009-06-25
> **Subban said:**
> Of course linux can "do email", wanna bet that linux runs the majority of the worlds email ?

Provided you have configured your PC and router correctly which will be no doubt established shortly, I would warn against being absolutly cock sure that your ISP isn't blocking port 25 as it is fairly standard for them to do so as an anti spam measure in my experience. I have previously been told point blank by an ISP tech support they do not block outgoing port 25, to only find that they certainly did.

```
telnet smtp.address.you.use 25
```

If it connects then it is not blocked, if it doesn't then it is blocked. Takes all of 30 seconds to find this out.

---

### Post by mark.giblin on 2009-06-26
Don't take this the wrong way but I am fed up of repeating the same information over and over.

pop & smtp are on the same URI

> Dear Mark
 
I'm sorry to hear you are still experiencing difficulties with this.
 
But please note that the connection string will not be particular to our set up because as I mentioned we are not doing anything specifically to interfere with that.

Not qiute sure what they were on with the connection string but, I mentioned I have had a string of connection issues... But anyway...

I have trouble shooted this with the web host and seeing as webmail services can connect and I can only part conect then the issues with the local machine.

I have checked the firewall settings. SMTP is allowed.

The ISP does does not block anything, it is a basic internet connection, you get no host services other than an internet connection that allows you to connect to any of your chosen online services like web host space and email servers.

When you can collect but not send... Only one thing left to look at, the local config.

As I can not find anything wrong with the settings in any of the email clients I have tried, this means that the issue is at system level and out of my depths, so the issue needs either solving by some mirical update or help here in getting to the bottom of the issue rather than this focus on whos what and where to pass the buck and live in denial that linux is stuffing things up for once.

Please focus on the issue being an issue with the "Default" install of linux Ubuntu 8.10 intrepid ibex... something clearly is wrong and I am asking for serious help and instead I am being flanneled with this finger pointing exercise that I have ruled out as I have tried resolving this by FAQ, web searches lots of phone calls to the web host and eventually here.

So please, I need help on this.

---

### Post by t4thfavor on 2009-06-26
Try setting up an MX record with your DNS provider. Thats where all of my problems were solved. If you already did that, make sure its correct. Its easy to screw up if your new to email servers.

---

### Post by mark.giblin on 2009-06-28
Sorry but AGAIN the issue is the "LINUX" install.

This has been the issue from the start.

IT IS NOT anything to do with DNS or issues with my ISP or the web host or anything other than the actual operating system.

The Ubuntu 8.10 install is a default install, it did not work sending emails but only collecting emails so I looked in the many help files and found one that stated that the issue is in sendmail and I should install the MTA client. I did and it did not resolve the issue.

The issue is something on this operating system is blocking outgoing connections for smtp despite the port being open and ready for outgoing traffic to the mail servers.

What I think people can not get their heads around is that I can collect by pop and imap but not send despite the URI for the mail servers are EXACTLY THE SAME ADDRESS.

If I can collect but not send, law of logic dictates the issue is on the machine, not the host or ISP.

I can plug this modem in to Mr Laptop that rund windows and same browser (Opera) and Opera mail will send and collect.

So by process of elimination I have exhausted all possible issues and that only leaves one left.

UBUNTU.

Some setting or bug issue in the config and no one as yet has indicated where I find the config for checking what the settings are but instead I am given the round robin on every reason why it is not Linux when the answer is as plain as the nose on your face.

Sorry if I sound pissed but you would be too if you have repeatedly asked but fobbed off with every excuse under the sun.

Now can someone please try resolving this based on the issue being an outgoing connection isse despite the firewall having the setting for smtp allowed. Funny thing is that the firewall has no setting for pop yet it has no issues collecting emails...

---

### Post by howefield on 2009-06-28
> **mark.giblin said:**
> Now can someone please try resolving this based on the issue being an outgoing connection isse despite the firewall having the setting for smtp allowed.

Why don't you just start answering the questions asked of you instead of spouting off, you will end up with egg on your face by blaming Ubuntu for your own inadequacies.

Let's start with the questions posed by ACupOfCoffee ?

---

### Post by DeMus on 2009-06-28
Mark, of course you are pissed of, everybody would be when having trouble like you have now. But, and this is really true: everybody here on the forum wants to help you, as long as you let them help you. You have to give some information for others to help you.
Now, the second poster, his name is ACupOfCoffee, asked you some questions. Please answer them and people can see what needs to be done to make your e-mail work.
You ask for help by coming here, then when things don't work instantly you get angry. Don't do that. Remember we are all volunteers, loving Linux and especially Ubuntu, nobody gets paid for helping you, we all do this because we believe in using Linux.

---

### Post by Sidewinder1 on 2009-06-28
What email client? (Firefox, Opera, Thunderbird, Evolution,...or the like?)
What Web-mail Host? (Hotmail, Gmail, Yahoo-mail,...or the like?
What internet connection? ( Broadband, 56K modem, wireless or ethernet, or the like?)
With these answered accurately, the volunteers here can begin to help you solve your problem, as I'm sure they will... It's probably a simple configuration issue that you've not come across, no disrespect intended.
HTH,
Side

---

### Post by mark.giblin on 2009-06-30
> **howefield said:**
> Why don't you just start answering the questions asked of you instead of spouting off, you will end up with egg on your face by blaming Ubuntu for your own inadequacies.

Let's start with the questions posed by ACupOfCoffee ?

BECAUSE... I have.

My ISP has NO BLOCKING
My ISP does not BLOCK PORTS.
My Host has confirmed that I am correct about ther connection issue because theirs no actual record of any connection other than POP.
The problem has been troubleshooted before asking here again.

SO what was the purpose of your insult?

---

### Post by lisati on 2009-06-30
> **mark.giblin said:**
> BECAUSE... I have.

My ISP has NO BLOCKING
My ISP does not BLOCK PORTS.
My Host has confirmed that I am correct about ther connection issue because theirs no actual record of any connection other than POP.
The problem has been troubleshooted before asking here again.

SO what was the purpose of your insult?

I have read the whole thread so far, and you appear not to have answered this question (and others): What email software are you using?

---

### Post by lisati on 2009-06-30
Maybe a link to where the OP has asked for help before? Is this the one [http://ubuntuforums.org/showthread.php?t=1130729](http://ubuntuforums.org/showthread.php?t=1130729) ?

---

### Post by mark.giblin on 2009-06-30
> **DeMus said:**
> Mark, of course you are pissed of, everybody would be when having trouble like you have now. But, and this is really true: everybody here on the forum wants to help you, as long as you let them help you. You have to give some information for others to help you.
Now, the second poster, his name is ACupOfCoffee, asked you some questions. Please answer them and people can see what needs to be done to make your e-mail work.
You ask for help by coming here, then when things don't work instantly you get angry. Don't do that. Remember we are all volunteers, loving Linux and especially Ubuntu, nobody gets paid for helping you, we all do this because we believe in using Linux.

I have already repeated the provider and other information requested many times before (available from my user profile) and TBH "NO ONE" is helping because they have got this "FIXED" notion that the issue is nothing to do with the OS install when it has EVERYTHING to do with it. This issue has existed from install.

If I can get a connection in from the host on mail.mydomainname.tld and smtp is on the same mail.mydomainname.tld URI, what could be the issue, Hmmmm let me see, Hmmmm, seems that the moon is the wrong phase and its high tide on Brighton Beach.

I will say again, the issue is in a "CONFIGUATION" setting on the Linux install I have, nothing to do with the actual email clients as I have tried several now and all have the same problem, POP incoming is OK but SMTP out is not happening and it is being blocked on this machine and its not a firewall issue. I keep getting messages from the system that the domain name for this machine is not qualified. !! WTF is that bx about?

MX records in the host? Nothing like that is avaiable via the cPannel as that is taken care of by the host, I can make and delete mail boxes on the domain I own but that is it.

DNS? I do not need DNS, that is controlled by my web host and same for the hosts DNS, the ISP I have resolves names promptly, nothing is interfering with my ability to connect to the internet and use the web, when I run my Windows Lappy, with the same software (Opera) it has no issues with collection and sending.

The modem I have is a HSDPA modem, if you do not know what type that it, look it up. With these modems your a direct internet connection with nothing blocking you, you get no email accounts just a straight forward internet service with no frills.

So you will soon get t understand that I have tried the all sorts of ways of getting this resolve and were going in circles and if what you say was true, then people would read, comprehend and then understand that I have spend time on the phone to the web host that cost me an arm and a leg and same for the ISP I have, they are costly phone calls to.

So I have eliminated the Two likely sources of the problem and its all pointing to this install of Ubuntu.

So unless people are going to post up how to get in to the config settings of ubuntu, were not going to get anywhere with this.

telnet resolves the address to an IP but then tries to connect to that address on the given port and it just sits and does nothing.

So I give up.

Would someone like to point the finger elsewhere? I would put money down at william hills with very short odd that the problem is just as I have been barking on about, a config setting in the OS. Prove me wrong and the beers are on me.

---

### Post by 3rdalbum on 2009-06-30
> **mark.giblin said:**
> So unless people are going to post up how to get in to the config settings of ubuntu, were not going to get anywhere with this.

That's why we're asking what e-mail client you are using! There is no system-wide configuration panel for e-mail, it is specific to the e-mail program that you are using.

Evolution (preinstalled on Ubuntu), Thunderbird, Opera, Seamonkey, Kmail? Which one are you using?

I'm going to throw out a suggestion here: If you are using Evolution, it gives you the **choice between many different forms of logging in, and the choice between two different forms of encryption** (plus "no encryption") for login details. This is true for sending e-mails, not just recieving them.

I have attached a screenshot from the Evolution preferences panel. **If the settings are wrong, your e-mail client can't connect to your ISP.** Usually an ISP will support a number of different methods, but I know that some ISPs support JUST ONE combination. **This may require some trial and error.** The default Evolution setting is what the setting should most commonly be, but some ISPs vary in what they support.

I understand that you're frustrated, but Ubuntu has perfect e-mail capability that is as good for home use as it is for large-scale enterprise. There's only one possible flaw: You must have it set up right in order to work. If you can tell us what the settings you have are, and what e-mail program you are using, we can determine how correct those settings are. Just because the settings "look right" to you, it does not mean that they are right. I mean, I think I'm a fairly attractive-looking guy, but no girls want to go out with me; so a second opinion can help.

---

### Post by lisati on 2009-06-30
I have a hunch the OP might be using Opera, based on this post from another thread: [http://ubuntuforums.org/showpost.php?p=7149892&postcount=9](http://ubuntuforums.org/showpost.php?p=7149892&postcount=9)

---

### Post by Subban on 2009-06-30
> **mark.giblin said:**
> telnet resolves the address to an IP but then tries to connect to that address on the given port and it just sits and does nothing.

So I give up.

For all your bluster, this is actually about the only useful piece of information I have seen that might be helpful despite people repeatedly asking, unless I am greatly mistaken.

If telnet cannot connect on that port, then something is likely blocking it? ISP, router, firewall config or something else.

You are spending longer arguing with people about it being a problem with your install and no-one "gets it", when no-one has said its NOT a problem with your install, they are just asking for information to try and narrow down what needs to be reconfigured, whether its your firewall or even what email client it is you are using!

Yes you have a problem, yes a lot of people despite your attitude are here STILL trying to help, but for the love of god help people to help you.

---

### Post by Cuba71 on 2009-06-30
I can't understand what's so difficult about answering the question regarding what mail client is he using.

---

### Post by mark.giblin on 2009-07-01
> **3rdalbum said:**
> That's why we're asking what e-mail client you are using! There is no system-wide configuration panel for e-mail, it is specific to the e-mail program that you are using.

Evolution (preinstalled on Ubuntu), Thunderbird, Opera, Seamonkey, Kmail? Which one are you using?

I'm going to throw out a suggestion here: If you are using Evolution, it gives you the **choice between many different forms of logging in, and the choice between two different forms of encryption** (plus "no encryption") for login details. This is true for sending e-mails, not just recieving them.

I have attached a screenshot from the Evolution preferences panel. **If the settings are wrong, your e-mail client can't connect to your ISP.** Usually an ISP will support a number of different methods, but I know that some ISPs support JUST ONE combination. **This may require some trial and error.** The default Evolution setting is what the setting should most commonly be, but some ISPs vary in what they support.

I understand that you're frustrated, but Ubuntu has perfect e-mail capability that is as good for home use as it is for large-scale enterprise. There's only one possible flaw: You must have it set up right in order to work. If you can tell us what the settings you have are, and what e-mail program you are using, we can determine how correct those settings are. Just because the settings "look right" to you, it does not mean that they are right. I mean, I think I'm a fairly attractive-looking guy, but no girls want to go out with me; so a second opinion can help.


ANY OF THEM... Evoloution, Opera, take your pick. The issue is not the actual software but in the OPERATING SYSTEM or comonent config.

---

### Post by mark.giblin on 2009-07-01
> **Subban said:**
> For all your bluster, this is actually about the only useful piece of information I have seen that might be helpful despite people repeatedly asking, unless I am greatly mistaken.

If telnet cannot connect on that port, then something is likely blocking it? ISP, router, firewall config or something else.

You are spending longer arguing with people about it being a problem with your install and no-one "gets it", when no-one has said its NOT a problem with your install, they are just asking for information to try and narrow down what needs to be reconfigured, whether its your firewall or even what email client it is you are using!

Yes you have a problem, yes a lot of people despite your attitude are here STILL trying to help, but for the love of god help people to help you.

Well with all my experience of computers, th conectivity issue is simple.

ONE URI for connecting to smtp and pop, pop in is OK but smtp out is being blocked at system level. I can see errors that occur at the same time as I attempt to send email and it is the sendmail component bitching about my machine name is not a qualified name.

SO... if telnet conected to the server, why does the sendmail portion fail? IMHO its a config issue IN THE OPERATING SYSTEM and NOT the email client as everyone is latching on to.

---

### Post by lisati on 2009-07-01
> **mark.giblin said:**
> Well with all my experience of computers, th conectivity issue is simple.

ONE URI for connecting to smtp and pop, pop in is OK but smtp out is being blocked at system level. I can see errors that occur at the same time as I attempt to send email and it is the sendmail component bitching about my machine name is not a qualified name.

SO... if telnet conected to the server, why does the sendmail portion fail? IMHO its a config issue IN THE OPERATING SYSTEM and NOT the email client as everyone is latching on to.

I'm feeling a bit lazy to check back through this thread again to see if this has been touched on, but here goes:

IMO it's more likely to be your firewall settings than the Operating Sytem *per se*. I'm sure there's some [s]victim[/s] volunteer who is happy to help you with this.

Failing that, is changing your machine's name an option?

---

### Post by Subban on 2009-07-01
> **mark.giblin said:**
> Well with all my experience of computers, th conectivity issue is simple.

ONE URI for connecting to smtp and pop, pop in is OK but smtp out is being blocked at system level. I can see errors that occur at the same time as I attempt to send email and it is the sendmail component bitching about my machine name is not a qualified name.

SO... if telnet conected to the serve

You said previously telnet did NOT connect, it resolves the IP but will not connect on the port, you didn't give info on which address or port so we can only assume its the correct one, most likely it is. This would suggest its either your firewall or ISP.


> why does the sendmail portion fail? IMHO its a config issue IN THE OPERATING SYSTEM and NOT the email client as everyone is latching on to.

Are you actually using Sendmail (this is an actual program, or when you say sendmail do you mean "sending mail"?

If yes then I am out of my depth by some margin here, but doesn't using an MTA work differently to just using an email client internet traffic wise. Because I am fairly sure most ISP's block outgoing mail traffic from their customers machines in the UK to help reduce spam from misconfigured MTA's.

You have said your internet access is unfiltered, but I can safely say that unless you are paying a sizable chunk each month (my own is £50ppm  from Demon for no traffic shaping or transfer limits/quotas), it most certainly is not a direct, unfiltered and unmanaged connection. I'm going out on a limb a little but you have 2g/3g connection or something is that right, I think I'm safe in saying that running an MTA on such a connection wouldn't be normal.

Do you run an MTA on your windows install you have mentioned?
Do you actually need one on Linux on a mobile connection?

My money is still on firewall or if using Sendmail the ISP blocking outgoing, unless you can tell us which ISP or whether you use an MTA on Windows successfully.

---

### Post by mark.giblin on 2009-07-01
> **lisati said:**
> I'm feeling a bit lazy to check back through this thread again to see if this has been touched on, but here goes:

IMO it's more likely to be your firewall settings than the Operating Sytem *per se*. I'm sure there's some [s]victim[/s] volunteer who is happy to help you with this.

Failing that, is changing your machine's name an option?

It is not a firewall issue, SMTP is allowed in the firewall. I have already explained this.

---

### Post by mark.giblin on 2009-07-01
> **Subban said:**
> You said previously telnet did NOT connect, it resolves the IP but will not connect on the port, you didn't give info on which address or port so we can only assume its the correct one, most likely it is. This would suggest its either your firewall or ISP.

IT IS NOTHING TO DO WITH EITHER, I DO NOT KNOW HOW MORE CLEAR IN THIS I CAN BE............................ 

Why do I need to give you the connection details? So someone here can attempt to send spam from my account!!! Think again.

> Are you actually using Sendmail (this is an actual program, or when you say sendmail do you mean "sending mail"?

If yes then I am out of my depth by some margin here, but doesn't using an MTA work differently to just using an email client internet traffic wise. Because I am fairly sure most ISP's block outgoing mail traffic from their customers machines in the UK to help reduce spam from misconfigured MTA's.

You have said your internet access is unfiltered, but I can safely say that unless you are paying a sizable chunk each month (my own is £50ppm  from Demon for no traffic shaping or transfer limits/quotas), it most certainly is not a direct, unfiltered and unmanaged connection. I'm going out on a limb a little but you have 2g/3g connection or something is that right, I think I'm safe in saying that running an MTA on such a connection wouldn't be normal.

MY ISP CONNECTION IS A DIRECT CONNECTION.

MY WEB HOST is on SHARED SPACE with unlimited bandwidth and allowance and wher you get £50 from a month... Mine is £30 all in per year.
> 
Do you run an MTA on your windows install you have mentioned?
Do you actually need one on Linux on a mobile connection?

WINDOWS IS ON A COMPLETELY DIFFERENT SYSTEM. UBUNTU IS ON A CMPLETELY DIFFERENT SYSTEM.

AS FOR INSTALLING THE MTA CLIENT... I WAS FOLLOWING THE FAQ IN THE UBUNTU ONLINE HELP. I INSTALLED THE MTA CLIENT AS I WAS INSTRUCTED TO DO SO TO RESOLVE THE ISSUE. It didn't...
> My money is still on firewall or if using Sendmail the ISP blocking outgoing, unless you can tell us which ISP or whether you use an MTA on Windows successfully.

I HAVE REPEATED THIS HUNDREDS OF TIME THE "ISP" IS NOT, I REPEAT AGAIN IS NOT BLOCKING ANYTHING. THEY HAVE NO REASON TO.

UNLESS SOMEONE IS GOING TO ANSWER MY QUERY ON WERE I SET THE CONFIG SO I CAN GET OUTGOING CONNECTION, DON'T BOTHER POSTING A REPLY.

THE ISSUE IS WITH UBUNTU.

My faith in ubuntu is diminishing rapidly and I am getting fed up of answers the problem that have already been exhausted and likewise with querys about the email client, host, ISP.

It is something on this install that is blocking and it is nothing to do with the firewall. An I would like to know how you config the OS to stop this diversion of the connection. Some process is running that clearly shouldn't.

---

### Post by alphacrucis2 on 2009-07-01
> **mark.giblin said:**
> It is not a firewall issue, SMTP is allowed in the firewall. I have already explained this.

Well something is blocking it. There is nothing magic about smtp, it's just a connection to tcp port 25 which is what telnet blah.com 25 is doing and failing to connect from what you said. What do you get from:

```
iptables -L
```

---

### Post by mark.giblin on 2009-07-02
> **alphacrucis2 said:**
> Well something is blocking it. There is nothing magic about smtp, it's just a connection to tcp port 25 which is what telnet blah.com 25 is doing and failing to connect from what you said. What do you get from:

```
iptables -L
```

Thank you for your reply, it is something different than the others and here is the result...

> **********@**********-desktop:~$ iptables -L
iptables v1.4.0: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.


where ********** is the machine ID and my User ID.

As far as I am aware, I am root. So this says something is wrong to me.

---

### Post by Elfy on 2009-07-02
```
sudo iptables -L
```

I've read through the whole thread and while you might feel you are answering questions they are amongst a lot of text.

What was the answer to this question on your other thread - [http://ubuntuforums.org/showpost.php?p=7260482&postcount=13](http://ubuntuforums.org/showpost.php?p=7260482&postcount=13)

I have removed some of the posts, please keep it civil.

@mark.giblin - if people ask questions - please answer them simply - not everyone on the fourm has English as a frist language.

---

### Post by PureLoneWolf on 2009-07-02
I kind of skipped over the thread, but I couldn't see any reference to anything other than the OP trying to connect to a particular mailserver.  

Seeing as I have had many issues in the past with my own server allowing windows connections, but not linux...only to ultimately discover that there was a setting on the server that needed to be changed... I would highly recommend trying to use a free smtp server to see if you can do anything...

[http://lifehacker.com/111166/how-to-use-gmail-as-your-smtp-server](http://lifehacker.com/111166/how-to-use-gmail-as-your-smtp-server)

With the link above, you can sign up for a free Gmail account and then use it through Thunderbird/Evolution etc.

I realise that you are (quite angrily) insistent that the fault lies with the "default" ubuntu installation, but seeing as I have installed onto around 10 different machines for people with different ISPs and mail accounts over the last 4 weeks and not had a single email issue...it seems a little strange.  Not impossible, but strange.

---

### Post by mark.giblin on 2009-07-02
> **forestpixie said:**
> ```
sudo iptables -L
```

I've read through the whole thread and while you might feel you are answering questions they are amongst a lot of text.

What was the answer to this question on your other thread - [http://ubuntuforums.org/showpost.php?p=7260482&postcount=13](http://ubuntuforums.org/showpost.php?p=7260482&postcount=13)

I have removed some of the posts, please keep it civil.

@mark.giblin - if people ask questions - please answer them simply - not everyone on the fourm has English as a frist language.

TBH, I have gone around in that many circles, I will have to fire it up again, so... I will not only repeat the test but also give Jaunty a go too as I just got a copy burned to CD.

Be back in a bit.

Cheers.

---

### Post by kameelperdza on 2009-07-02
can one of you smart email people please help me with this
 
[http://ubuntuforums.org/showthread.php?p=7550893#post7550893](http://ubuntuforums.org/showthread.php?p=7550893#post7550893)

---

### Post by mark.giblin on 2009-07-02
Well I tried this under both Intrepid and Jaunty Live CD's.

I could under both CD's acess incoming emails using Evoloution mail client but sending emails was not happening.

This is the output from the terminal
> **********@**********n-desktop:~$ sudo iptables -L
[sudo] password for **********: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:imap2 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT]: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
**********@**********-desktop:~$ 


Which means nothing to me but going through it I noticed this line.

> target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp

Which I take it to mean that the destination 'annnywhere' means that smtp is not blocked on my local machine, which im my books would mean that the issue(s) is in the component(s) that handle the internals.

How would I be able to check what system components are correcty configured?

---

### Post by The Cog on 2009-07-02
The only other component is your email client, which you still seem reluctant to discuss. 

Can you please try this experiment: Open a terminal and use the command:
**sudo tcpdump -lnp**
This outputs a list of all the packets leaving and entering your PC. Leave the command running while you try to send an email. Then post the results here. It will enable us to see how far the outgoing mail connection is getting - whether the connect request is actually being sent, whether it is being accepted, which end breaks the connection. This trace will show us the IP address/domain-name of your email provider, but not your login name or password. Hope that's OK by you.

Also, tell us if there is any error message from your mail client (and what it says of course). Please wait at least 5 minutes if it appears to be trying unsuccesfully to connect.

---

### Post by alphacrucis2 on 2009-07-03
> **mark.giblin said:**
> 


Which means nothing to me but going through it I noticed this line.

```
ACCEPT tcp -- anywhere anywhere tcp dpt:smtp
``` 



That line isn't relevant as it checking a destination in the INPUT chain. The important thing is that the INPUT chain includes a table that has this:

```
ACCEPT all -- anywhere anywhere ctstate RELATED,**ESTABLISHED** 
```

That means that any input that connection-tracking considers to be part of an established connection will be allowed in. The OUTPUT chain pretty much allows anything from what I can see (has ACCEPT as a default policy) so you would have to explicitly DROP or REJECT. I would say that Netfilter isn't blocking the SMTP. BUT things could go wrong if for some reason the ip_conntrack module isn't loaded.(Unlikely as then web browsing wouldn't work either). At this stage I would follow The Cog's suggestion of running a tcpdump packet capture as that will show whether or not the SMTP SYN packet is being transmitted.


Another thing to try as a quick test in case I missed something in your iptables -L output. Issue the following command:

```
sudo iptables --policy INPUT ACCEPT
```

Then try your smtp connection. When finished change the policy back again:

```
sudo iptables --policy INPUT DROP
```

Report results back here.

---

### Post by mark.giblin on 2009-07-04
> **The Cog said:**
> The only other component is your email client, which you still seem reluctant to discuss. 

Can you please try this experiment: Open a terminal and use the command:
**sudo tcpdump -lnp**
This outputs a list of all the packets leaving and entering your PC. Leave the command running while you try to send an email. Then post the results here. It will enable us to see how far the outgoing mail connection is getting - whether the connect request is actually being sent, whether it is being accepted, which end breaks the connection. This trace will show us the IP address/domain-name of your email provider, but not your login name or password. Hope that's OK by you.

Also, tell us if there is any error message from your mail client (and what it says of course). Please wait at least 5 minutes if it appears to be trying unsuccesfully to connect.

> sudo tcpdump -lnp
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes


Which is not helping because I am on a HSDPA modem that connects via USB.

So if mailsend is looking to go ethernet, it will fail 100%, it however does not explain how I am able to collect emails.

---

### Post by alphacrucis2 on 2009-07-05
> **mark.giblin said:**
> Which is not helping because I am on a HSDPA modem that connects via USB.

So if mailsend is looking to go ethernet, it will fail 100%, it however does not explain how I am able to collect emails.

Just tell tcpdump which interface to use. It defaults to eth0 and I assume the Cog thought you were using ethernet. If you want want to get this sorted you are going to have to use a little initiative yourself. For example if I want to see what is going in and out of my wireless connection I would run tcpdump like this:

```
sudo tcpdump -i wlan0 -lnp
```

The -i wlan0 tells tcpdump to capture data going through interface wlan0. All you had to do is figure out what interface id your usb modem is using. You can figure this out by:

```
ifconfig
```

Which will list all the network interfaces. Shouldn't be too hard to figure out which is the right one. Also when you have finished you stop tcpdump by doing a CTRL c

By the way did you try the temporary INPUT chain policy change I suggested?

---

### Post by mark.giblin on 2009-07-05
Sorry I didn't try it yet.

As I am a newbie to linux, it is better to crawl before I run and to try too many things at once only confuses the issue as I would like to understand the process and what relates to what otherwise I would get lost and my head may explode from information overload.

I can not understand why the developers do not code in a routine to find the appropriate adapter, ether or usb and if its confused to ask the user. I am assuming that this may solve the issue.

I will get back to you soon on this as I need to give the nurons a rest as they havent had a day off for a couple of months...

---

### Post by alphacrucis2 on 2009-07-05
> **mark.giblin said:**
> Sorry I didn't try it yet.

As I am a newbie to linux, it is better to crawl before I run and to try too many things at once only confuses the issue as I would like to understand the process and what relates to what otherwise I would get lost and my head may explode from information overload.

I can not understand why the developers do not code in a routine to find the appropriate adapter, ether or usb and if its confused to ask the user. I am assuming that this may solve the issue.

I will get back to you soon on this as I need to give the nurons a rest as they havent had a day off for a couple of months...

Just to make it clear, the tcpdump isn't to solve the issue, it is to obtain information about what is actually happening. On the other hand my suggestion of quickly setting the INPUT chain policy to ACCEPT is worth a try as a quick attempt to fix the issue.

---

### Post by The Cog on 2009-07-06
This command:
```
sudo tcpdump -i any -ln
```
will listen on any interfaces you have. Sorry, I should have thought of that.

---

### Post by Zack McCool on 2009-07-06
> **mark.giblin said:**
> Sorry I didn't try it yet.

As I am a newbie to linux, it is better to crawl before I run and to try too many things at once only confuses the issue as I would like to understand the process and what relates to what otherwise I would get lost and my head may explode from information overload.


If you're a newbie, you'd think you'd be a little more civil to the people trying to understand your issue and walk through basic troubleshooting with you.


Anyhow, have you actually tried telnetting to the mail server?  What was the result?

```
telnet smtp.mailserver.com 25 
```

Where smtp.mailserver.com would be replaced by your actual mailserver.

If you get anything but a positive reply (usually something like "Connected to smtp.mailserver.com (xx.xx.xx.xx)") Then you are NOT connecting.

Also, I understand your reluctance to give out the name of your mail host, but simply with that information, nobody can spam from your account.  Giving that information may help people to actually help you.  You need to understand this:  The problem is not with Ubuntu (or Linux).  The problem is 100% the configuration of your e-mail client, or blocking at the ISP level.  The OS does NOT control outgoing smtp connections (outside of a firewall when you have one configured).  

Your previous responses make me hesitant to even TRY helping you, and if you respond to my inquiries in the same manner, I won't bother.  But understand that most of the people attempting to help you DO know what they are talking about.  They need help from you to help you.  Personally, I am not only certified in Linux Engineering and Administration, but also do it professionally.  I administer internet access and e-mail servers for a large corporation.  If I am unable to help you find the answer, it will be because of lack of information.  The same likely goes for many of the people that have tried to help you in this thread.

So, please give us the information we need, and don't tell me about other threads, or what the ISP or mail company said.  That information isn't helpful, and I really just want to help you get your system running right, but will not bother if you don't want to give the necessary information, in a civil manner.

---

### Post by megamania on 2009-07-06
> **Zack McCool said:**
> If you're a newbie, you'd think you'd be a little more civil to the people trying to understand your issue and walk through basic troubleshooting with you.

Just so you know, after writing something like that in this thread I received an unofficial warning and my messages were jailed because they had a potential to start flames.

It's the first time in 4 years that I don't feel comfortable writing in these forums. I know, I'll probably burn in Ubuntu-hell for sinning again.

---

### Post by The Cog on 2009-07-06
Once in a while someone with attitude like that gets it sorted with the forums help, and suddenly becomes very grateful once the frustration goes. That makes it worth trying, at least for a while.

---

### Post by mark.giblin on 2009-07-17
> **alphacrucis2 said:**
> Just tell tcpdump which interface to use. It defaults to eth0 and I assume the Cog thought you were using ethernet. If you want want to get this sorted you are going to have to use a little initiative yourself. For example if I want to see what is going in and out of my wireless connection I would run tcpdump like this:

```
sudo tcpdump -i wlan0 -lnp
```

The -i wlan0 tells tcpdump to capture data going through interface wlan0. All you had to do is figure out what interface id your usb modem is using. You can figure this out by:

```
ifconfig
```

Which will list all the network interfaces. Shouldn't be too hard to figure out which is the right one. Also when you have finished you stop tcpdump by doing a CTRL c

By the way did you try the temporary INPUT chain policy change I suggested?

The HSDPA modem is one of these things: [http://www.three.co.uk/Mobile_Broadband](http://www.three.co.uk/Mobile_Broadband)

I tried the tcpdump and plugged in usb0 which is what the HSDPA modem is on despite it being listed as "tcpdump: SIOCGIFHWADDR: No such device"

As for figuring it out, I have figured it out to be an operating system issue and it is something that is out of my control or access.

So currently this is out of my hands and in the hands of Ubuntu to do something about it.

As I have tried using live CD's as well to trouble shoot this issue, it appears to exist in both live CD's of Intrepid and Jaunty, this is much like the APTonCD program that ( I had investigated and found) was faulty for 3 Ubuntu releases.

Question is, who is it that decides on what is more important, programs functioning or how the operating system desktop looks?

I appreciate peoples efforts in trying to help but ... Ubuntu now needs to look at its source code to rectify this problem as it is clearly a programming issue when you consider that internet works, emails can be fetched but the other side of the coin, things are not functioning properly or theirs been too many assumptions made about the clients machine use... What I do not understand is how a mailsend routine can not pick up on the fact that the modem is on a USB port when the mailfetch routines do...

Thanks for all your help but its not going anywhere and it is very clear that this issue is only going to be solved at system level.

---

### Post by Zill on 2009-07-17
mark.giblin:  I know you are frustrated by this but ranting about Ubuntu really doesn't help :-)  You seem very reluctant to actually provide the information requested earlier in this thread.  If you supply the information people have asked for then it is quite likely that this problem can be resolved.

You have given a link to [www.three.co.uk](www.three.co.uk) but the help section of this site reveals that six different usb modems may be supplied:
Huawei E169
Huawei E160G
Huawei E220
Huawei E169G
Huawei E156G
ZTE MF627

If you tell us which one you are using, **along with your preferred email client**, then it may help resolution considerably ;-)

---

### Post by Zack McCool on 2009-07-17
> **mark.giblin said:**
> 
I appreciate peoples efforts in trying to help but ... Ubuntu now needs to look at its source code to rectify this problem as it is clearly a programming issue when you consider that internet works, emails can be fetched but the other side of the coin, things are not functioning properly or theirs been too many assumptions made about the clients machine use... What I do not understand is how a mailsend routine can not pick up on the fact that the modem is on a USB port when the mailfetch routines do...


Mail applications do not care where your modem is.  If you have tcp/ip, they use it.  They do not directly access a hardware port.

You have made it clear that you don't want help with your issue, but would rather point the finger and complain, so I guess I'll leave you to that.  If you decide you'd like to troubleshoot your issue, though, feel free to post some useful information here, and I'll jump back in.

---

### Post by mark.giblin on 2010-01-12
Pardon?

I am ranting because people here refuse to give me the information I need to resolve this but instead I am sent on a chase that is not proving very helpful in either direction.

If the issue is one of routing, what commands DO I need and where do I find those config files and maybe then we can take one step closer to resolving the issue.

As for your suggestion that I don't want the problem dealt with... where do you get off? That has to be the most idiotic comment I have herd to date. I really appreciate help when the question I ask is answered and not answered with another question and after reviewing many threads on this site, the attitude seems to be endemic across the board, people ask a perfectly logical question and it is answered with something completely unrelated.

a good analogy of this situation is I am at the DIY Shop asking for a tin of blue paint and I am being served flock wall paper... 

TBH I just wish someone in Ubuntu would get off their hands and poke whoever it is to sort out the tcp/ip routing issue ort can some one here tell me how to as the issue is nothing to do with the email clients, they collect emails all day withuout issue, sending them out invokes sendmail and it is sending email to a defunct lan card. How stooopid is that?

So can we get this resolved and be one happy family again?

Modem is the E220 which makes littel difference because several friends have different versions and they all use the same conectivity software under windoes, I know because my friend had the 160G and my E220 software was what installed and got his modem up.

---

### Post by Zill on 2010-01-12
mark.giblin:  I am reluctant to reply to your latest post due to your negative responses to all previous attempts to help you.  However...

A quick check of the Help section at [three.co.uk]("http://www.three.co.uk/Help_Support/Mobile_Broadband_Help") reveals the following advice:

> To protect you and our network, we restrict access to port 25 on our Mobile Broadband network.

If you use email software such as Outlook or Vista Mail and your email provider uses Port 25 for outgoing mail, you will need to change your port or SMTP server when connected to our broadband network.

Errors you might see when trying to send email over Port 25 on our network include: SMTP 554 Transact Failed - Transaction failed; Port 25 error; The connection to the server has failed- Error Number: 0x800CCC0E; or the sending of email will time out.

If you have one of these error messages the best option is to change the outgoing email port from 25 to 587. It is possible that your email provider does not support port 587 - in which case you should try port 465 as an alternative.

This indicates that *may* need to include a different port number, such as 587, in your smtp server address. eg.
```
smtp.my.server:587
```
Hope this helps.

---

### Post by mihamil on 2010-01-13
Is there a particular reason you are using sendmail.  Have you tried configuring evolution's "Sending Email" settings to use smtp and point the server information to your ISP's mail server.  If your ISP is indeed not blocking port 25 this should work.  Also please make sure they do not require authorization for outgoing email.  If so provide it in the boxes below.

MH

---

