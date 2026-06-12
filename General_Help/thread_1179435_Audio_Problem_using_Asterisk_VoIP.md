---
title: "Audio Problem using Asterisk VoIP"
date: 2009-06-05
forum: General Help
---

### Post by blackxored on 2009-06-05
Hi. 
I know it's hard to say for sure, but I have this problem when installing an asterisk server, after connecting clients, there is this audio echo or something, e.g. I get this terrible noise, and since I've been assigned to install this server, I need to know if there's something I can do on the server side to correct the situation; if there isn't at least then have the basis to say the problem is client-side only. Please provide some help, we've tested using ekiga for linux and x-lite and windows messenger for windows, all with the same problem. 
Greetings for all.

---

### Post by jonobr on 2009-06-05
Hello


Could you describe the problem a bit better.

What kind of noises are you hearing.
Is it scrathy or poppy or clicky...

The actual noise type indicates a lot of problems as it can point to jitter, latency, bandwidth or packetisation issues.

Also what would be really needed to help would be a trace of a sip call showing the RTP and SIP signalling.
I dont know if you would be willing to get that and post here?

Lastly, What you really need to do is have to clients on the same network as the sip server and ensure they work,
if they do , you know the problem is external.
If they dont, then the problem is internal

---

### Post by blackxored on 2009-06-08
Well,  it's actually metallic with a lot of static. And yes, the clients are in the internal network. I'd rather say isn't bandwith related because we're testing in machines in the same room, at the same LAN.

BTW: The Asterisk operator or whatsoever also it's played unproperly. When you call an unknown extension, the "caller isn't available message" its also played wrongly. It could be something to do with the linux drivers on the server LOL? Or maybe it's something relating asterisk configuration?

---

### Post by jonobr on 2009-06-08
Hello

On point 1- I agree chances are its not a bandwidth issue.
WIthout having any traces or details about whether different clients show differing results, I can only guess at the problem. T
 From what you describe it almost sounds as if you are using differing packet sizes or ptime in the media attribute  on the sip signalling 

This can result in what you hear.
What this means is that there are different packet times are being used on either end and the audio is rubbish.
The way to see ptime is to do a trace

```
sudo tcpdump -w trace.pcap -s 1600 -i any port 5060
```
Then open it in wireshark.
You should see a packet called an invite.
This invite has a message body.
In the message body you should see a lot of media attributes and one is ptime,
compare what they are on both ends.
Again, having a trace of an actual call would give a lot more detail

On the second question, it actually sinds like a registration issue.
When a client buts up it registers with the registrar.
The registrar contains the "whos available for a call" list 
If its not in there it will say its unavailable.

You need to check if the client is in the registrar if its not thats the problem.

Ill have a look around as to how to check the registrar on asterix.

The best way to see if your device is registering ok is to do
a tcpdump as above and open in wireshark.
When a device powers up you wills ee the registration go out and you should see a response packet that says 200ok.

If you want to post those traces directly to me, I could have a look at them for you.

---

### Post by blackxored on 2009-06-08
Ok, I'll check this ptime output right now. 
About the second issue, sorry if you misunderstood me, what I meant is that even that message "The user you're calling is unavailable", listens too badly. 
Do you know about any alternatives to Asterisk, to give a try?

---

### Post by jonobr on 2009-06-08
Hello


The only other thing you could try is the children of openser.
OPenser project has ended and forked into two other projects.

[Kamailio which is here]("http://www.voip-info.org/wiki/view/Kamailio") and [OPensips here]("http://www.voip-info.org/wiki/view/OpenSIPS").
Openser points to the opensips domain.


I used to work a lot with openser but have not worked with the later stuff.

I would really hold off for a while going to something else, as I believe you have accomplished quite a lot.
The trace you grab may show the reaosn for the problem, and as said, if you post it to me maybe I could help you

---

### Post by blackxored on 2009-06-08
Ok, sorry. I didn't understand a lot about your last post. I've attached the traces for a single class initiation and some audio sending/receiving.

---

### Post by jonobr on 2009-06-08
Hello

Thanks for the trace.

I see a few things I understand and some I dont.

Heres what I can see,

Your Ekiga  client  using version 3.2 and IP address 117 , registers with the  asterix server (.208 )

This is initially rejected (packet 6) which is ok and then accepted after authorization
Packet 10 (you will see it reports its bindings) This means its saying here is where I currently am.

There is then an odd notify at packet 17, saying "I have information on your voicemails"
Usually it does this to say it has new voice mails, but in this case ots says there are none.


I could make a few more comments , but the next interesting packet is your call
The invite to telephone 1002

You then see asterix respond with
'100 trying' (trying to place the call)
'180 ringing' (this tells the client to play ring tone to the caller)
And then a 200ok
This usually means the other end has picked up.

Then an ack,
At this point the audio (rtp) is set up in both directions

The important thing on sip is that the caller, presents what he is capable of in the invite, and in the 200ok from the calleee, it will say what it can accept.

Once the agree on protocols codecs and so on, they set up the call.

The thing thats bugging me about this is that a protocol is agreed ,
however your 200ok contains PCMA and PCMU (PCM companding for a law and mu law.
comapnding is how the voice is digitised from analog to digitial and recovered)

A law is used in Europe and mu is used in NA.

I see in the response that no companding is selected in the ack from the ekiga client

This "may" be where the problem is.
I am thinking both sides are selecting different companding.

Can you see a setting like that in your clients or asterix?

Im thinking this is causing your issue.

Lastly, I would also recommend you upgrade Ekiga.
the 3.2.0 used to drop calls for no reason.

Im attching the intersting bits in the trace.
note the ptime =20 (miliseconds)
the companding shows both.,


One additional comment (sorry for the long post :-(  )
Try using an xlite client to see if your seeing the same issue on that

---

### Post by blackxored on 2009-06-08
I've actually restricted audio codecs, if this is what you're talking me about. I've restricted allowed codecs to a subsect like speex, gsm, law, ulaw and the like, and once established ekiga shows me pcmu, yes. 

I've upgraded ekiga because another issue and doesn't solve it either. 
BTW, the audio problem is common among all clients I've tested, window versions of x-lite, windows messenger, linux ekiga, and linux twinkle.

---

### Post by jonobr on 2009-06-08
Hello


Try only using G711 codec,
GSM and the likes are heavy on compression/decmpression and processing.

G711 is 64k and should be the best quality.
Try with that one only and see how that works before moving to other codecs

---

### Post by blackxored on 2009-06-08
Sorry, maybe it's me. But after restricting to g711, I've got this:
> 
[Jun  8 22:32:10] NOTICE[24818] chan_sip.c: No compatible codecs, not accepting this offer!
in /var/log/asterisk/full
It doesn't let me call as you see.

EDIT:

Ok, let me tell you. Giving your codec-issue perspective, I've done some tweaking. 
Issuing the following:
> 
disallow=all
allow=**pcmu,pcma**,gsm,speex,h261,h263,ulaw,alaw


makes the so-called "operator" to play audio properly. As you may remember from this thread beginning that was another issue. So when I call the echo extension sip:500 the operator listens clearly. 

But I'm still testing the audio against clients, since I've been testing in the same room against a wifi-connected laptop. 

Suggestions are still welcome. 
BTW, giving some clearance, the server is asterisk-1.4.25 build from source, my client is ekiga-3.2.0ubuntu1 and the remote client is x-lite (I think it's 3).

---

### Post by jonobr on 2009-06-08
Hello

When setting the codec,
both sides have to support the codec.

If one side does not have it it will say so.

For example if I was calling you,
I would let you know I speak english and cantonese,
you could say you speak spansh and cantonese
Then we could mutually agree on cantonese

The same is true for sip,

Its like you set one side to say I speak english and the other to spanish and cantonese,
it will say there is no point continuing

---

### Post by blackxored on 2009-06-08
Sure, I'm aware about this protocol and codec initial negotiation. Actually, I wasn't receiving video because the remote client was only sending h323, not supported by ekiga. That was fixed already. Did you check my edit in the previous reply?

---

### Post by jonobr on 2009-06-08
Could you provide another trace, this time without the port 5060 in the tcpdump?
Im thinking if your getting this operator voice ok now then Im thinking its definately client config related.

Are you receiving the same bad audio on both sides? as well as the operator clearly on both sides?

---

### Post by blackxored on 2009-06-08
Ok. Here it is.
Actually, there is a lot of output, including from my LAN. So it doesn't fit.

---

### Post by jonobr on 2009-06-08
you forgot to attach

Also to add, I was looking at Asterik support of H323,
it appears only to support H323 as a gateway and not a gatekeeper.

---

### Post by blackxored on 2009-06-08
Actually, I didn't forgot. I said it doesn't fit. It's actually quite a lot of output for a couple of minutes. So I'm lost again.

---

### Post by jonobr on 2009-06-08
Hello


Could you do a filter and grab only the RTP and SIP traffic?

Or in wireshark, you can filter based on voip calls, it should show you the sip and RTP components.
or in the filter bar, type sip and hit enter.
SAve the result.

Then open up the file again and enter rtp

it should fitler out all rtp savew that again.

Hopefully that will work

---

### Post by blackxored on 2009-06-08
Here are the SIP and RIP packets. Hope its helps.

---

### Post by jonobr on 2009-06-08
Thanks for the repost,

Im not seeing RTP in the second trace, it says a lot of vtsas,
and other ports, but there is no vtsas.

COuld you try to refilter your RTP?

Also, on the SIp traces, im still seeing the two companding schemes,Im wondering if there should only be one based on your region?

Ill have to investigate that,

---

### Post by blackxored on 2009-06-08
I've refiltered again, it returns me the same output. The output I gave you is tested against the configuration I knew it was working (at least video and scaring audio), essentially a ```
bzr revert
```. Please keep that in mind. I'm not pretty sure if the audio problems I've experienced are codec-related now, since the audio passes, but it passes along with noise. I couldn't tell.

---

### Post by jonobr on 2009-06-08
Very Odd Im not sure what I am looking at with those traces.

Is there any way that you can force both sides to be mu law only?
Assuming your using Mulaw in the region you are in?

---

### Post by blackxored on 2009-06-09
Well, actually It supports ulaw and alaw only (Asterisk)

---

### Post by jonobr on 2009-06-09
Mmm...

Im really running out of ideas, the only other thing that I would normally recommned for an issue like this would be to fiddle around with the tx/rx gain. However , thats mostly evident on the pstn/ss7 links.

Im wondering if altering the gain here would affect this.

If that does show anything, Im thinking that maybe posting on the asterik support forum may help you out

Cheers

---

### Post by blackxored on 2009-06-09
Ok. Thanks for all the help. The topic isn't gone. I agree now it's codec related. This is after installing AsteriskNOW 1.5 on a VM:


```

**dpto-contaboc*CLI> core show codecs**
Disclaimer: this command is for informational purposes only.
    It does not indicate anything about your configuration.
        INT    BINARY        HEX   TYPE       NAME   DESC
--------------------------------------------------------------------------------
          1 (1 <<  0)      (0x1)  audio       g723   (G.723.1)
          2 (1 <<  1)      (0x2)  audio        gsm   (GSM)
          4 (1 <<  2)      (0x4)  audio       ulaw   (G.711 u-law)
          8 (1 <<  3)      (0x8)  audio       alaw   (G.711 A-law)
         16 (1 <<  4)     (0x10)  audio   g726aal2   (G.726 AAL2)
         32 (1 <<  5)     (0x20)  audio      adpcm   (ADPCM)
         64 (1 <<  6)     (0x40)  audio       slin   (16 bit Signed Linear PCM)
        128 (1 <<  7)     (0x80)  audio      lpc10   (LPC10)
        256 (1 <<  8)    (0x100)  audio       g729   (G.729A)
        512 (1 <<  9)    (0x200)  audio      speex   (SpeeX)
       1024 (1 << 10)    (0x400)  audio       ilbc   (iLBC)
       2048 (1 << 11)    (0x800)  audio       g726   (G.726 RFC3551)
       4096 (1 << 12)   (0x1000)  audio       g722   (G722)
      65536 (1 << 16)  (0x10000)  image       jpeg   (JPEG image)
     131072 (1 << 17)  (0x20000)  image        png   (PNG image)
     262144 (1 << 18)  (0x40000)  video       h261   (H.261 Video)
     524288 (1 << 19)  (0x80000)  video       h263   (H.263 Video)
    1048576 (1 << 20) (0x100000)  video      h263p   (H.263+ Video)
    2097152 (1 << 21) (0x200000)  video       h264   (H.264 Video)


```

I must solve with asterisk now, if not, I may desist.

---

### Post by jonobr on 2009-06-09
I would be interested to see which codec your using to contact your assistant,
(I think you mentioned that this clarity was good,) and the codec for the one that was not good,
are the same codec being used for each.

You can check this by doing
tcpdump -w trace1.pcap -s 1600 -i any port 5060
running the call to the auto attendant 

and then

tcpdump -w trace2.pcap -s 1600 -i any port 5060
and make the call to your client

You could post here again and I could compare these

---

### Post by blackxored on 2009-06-09
Ok. 
Admins tag this as SOLVED. 

Here is what I've done, it's actually a workaround and not a solution. But I think it quite worked. 
1. I setup VirtualBox to install AsteriskNOW (CentOS based).
2. I configured some extensions in Asterisk.
3. I set the following in FBX for all extensions:

> 
disallow=all
allow=ulaw,alaw,speex,gsm,h261,h263,h263p

4. All working OK.

Seems easy? It wasn't to get there.

---

### Post by jonobr on 2009-06-09
lol

Glad you got it working,

Also, I think you need to rename the thread as solved.

I would also edit your posts to remove the traces if you could

CHeers

---

