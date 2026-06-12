---
title: "ekiga registration failed"
date: 2009-04-16
forum: General Help
---

### Post by porchrat on 2009-04-16
Hi all

Trying to get ekiga running. Having an issue. I can't seem to get it to register, whenever I try it comes back to me with something along the lines of registration failed: Timeout. OK now to the details:

- I am registered at [www.ekiga.net](www.ekiga.net)
- I am sitting behind two NAT routers
- The ekiga NAT test detects a 'cone NAT' system.
- I have opened port 5060 for UDP, just in case
- I have no sip proxy settings entered in 'preferences'
- The STUN server I am trying to connect to is 'stun.ekiga.net'

Anyone have some suggestions?

---

### Post by aarceng on 2009-05-23
Similar problem. Maybe.
When I open Accounts I get
Ekiga.net ... Could not register(Unauthorized)
Ekiga Call Out ... Registered

But it seems I have to refresh the Ekiga Call Out each time.

I haven't got Ekiga working yet :confused:

---

### Post by kiridude on 2009-05-23
I agree, Ekiga should be easier to use - but hey, we can't complain about free beer...most people will simply use skype cuz it's easy.

Anyway, if you've got the time and patience, you'll most probably find the answer to your questions here: [http://wiki.ekiga.org/index.php/Main_Page](http://wiki.ekiga.org/index.php/Main_Page)

---

### Post by BrainwreckedTech on 2009-05-23
I'm gonna bump this because I have a similar problem, albeit in a slightly different situation

```
Internet <--> WEP Router <--> WAP Router
                  ^               ^
                  |               |
             Linksys PAP2T      Ekiga
             (Diamondcard)    (ekiga.net)
```

No matter what I do, I cannot get the PAP2T and Ekiga to work at the same time.  Before I got the PAP2T, Ekiga worked fine in this set up all by itself.  Afterwords, Ekiga won't work.

But I can get it to register.

I've set the PAP2T to use port 5000.
I've set WEP to forward port 5000 UDP to the PAP2T
I've forwarded ports 5060-5100 from WEP to WAP
I've set up port triggering on WAP so whichever computer wants  ports 5060-5100 at the time can grab 'em.
I've used gconf-editor to make sure ekiga is using the right ports in /apps/ekiga/protocols/ports.

Ekiga can register with my Ekiga account, but calling the Echo test results in "User is not available."

Close, but no cigar.  Ekiga needs some other ports, and without UPnP support, I can't tell what those ports are.

---

### Post by zbangash on 2009-05-23
Well.. My ekiga goes thru a funny cycle. 

I am not using an ekiga account.  I use an account of another service provider.

In my accounts info if I put registrar as ProxyXX.XXXXX.com, it goes thru 'registration timeout'.   If I change the account into to ProxyXX.XXXXX.com:5070, it does not even attempt to register, however as soon as I delete the :5070 part, it registers.  

So every time I start ekiga I have to go to accounts, add :5070 to the registrar, wait about a minute, then delete the :5070 and viola.. It registers. 

Sorry I'm a newb so I have no idea what I am talking about.. but this is how I made it work.

---

### Post by zbangash on 2009-05-23
> **BrainwreckedTech said:**
> I'm gonna bump this because I have a similar problem, albeit in a slightly different situation

```
Internet <--> WEP Router <--> WAP Router
                  ^               ^
                  |               |
             Linksys PAP2T      Ekiga
             (Diamondcard)    (ekiga.net)
```

.

well.. if I was you I'd put the both Ekiga and PAP2T on WAP.. forward all ports from WEP to WAP (DMZ, perhaps?).. and use port triggering to open ports.  But that's just me. 

Ekiga uses UDP 3478 and 3479 for trigger, and it asks for opening UDP 5000 to 5100.  

If your router accepts only one port for triggering (Dlink accepts range, Linksys accepts solo) use 3478.

---

### Post by BrainwreckedTech on 2009-05-23
> **zbangash said:**
> Ekiga uses UDP 3478 and 3479 for trigger, and it asks for opening UDP 5000 to 5100.

I'm pretty sure you're talking about STUN there.  Most documentation I've seen uses that as a trigger, yes.  But I have several things (PAP2T, Ekiga, Pidgin) that use STUN, so that can't be the trigger for Ekiga alone.

I've even fallen back to straight-up port forwarding with no results.

> **zbangash said:**
> well.. if I was you I'd put the both Ekiga and PAP2T on WAP...forward all ports from WEP to WAP (DMZ, perhaps?).. and use port triggering to open ports. But that's just me.

The reason I have this setup is for my Nintendo DS.  I don't want to compromise my entire network with the weaker WEP encryption.  With this setup, if someone breaks WEP, they only get access to my internet connection and some devices (DS, PAP2T) that aren't worth hacking.  If I DMZ the WEP router, that washes away the security.

I can easily get my Xbox 360's working under this double-NAT setup.  It was easy because the **Xbox 360 uses UPnP**, traverses the same ports in the same order every time, and **my router reports what's opening up what ports**.

Ekiga is a crap-shoot.  You can tell it what ports to use, but is it using them?  I've only ever seen ports 5060 and 5080 being used it what little I can understand from the debugging output.

Something else to think about is that Diamondcard service uses a SIP proxy.  Maybe this is the reason the PAP2T is working while Ekiga is not?

---

### Post by BrainwreckedTech on 2009-05-23
This is getting infuriating fast.

Turned off the PAP2T, went back to Ekiga, and Ekiga still doesn't work completely.  Which is odd -- I did a full test before switching from Vonage to Diamondcard, and part of that test was using Diamondcard through Ekiga.  But that was Ubuntu 8.10 and Ekiga 2.0.

Anyway, If I call myself using my cell phone, sound comes in cell phone --> Ekiga, but sound does not go out Ekiga --> cellphone.

I still have a computer with Ubuntu 8.10 on it brb.

**GUESS WHAT?!?!?!**  Ubuntu 8.10/Ekiga 2.0 works fine in my setup.  To my memory, Ubuntu 8.10/Ekiga 3.0SVN worked fine.  Ubuntu 9.04/Ekiga 3.2 is friggin' broken.  Who screwed the pooch and how?

I tried to mimic the old settings as much as possible.  I switched from PulseAudio to ALSA.  I copied over some keys in gconf-editor.  I even found out that Ekiga 2.0 was configured for RTP ports 5000-5059 and forwarded those ports (except 5000, still reserved for the PAP2T.)  N-O-T-H-I-N-G.

So, to answer porchrat...I throw in the towel on this one.  I hope you're not using Ekiga 3, but if you are go back to Ubuntu 8.10 for Ekiga 2.  If you were using Ekiga 2, I hope my rambling over router settings helped.

Port 1720 udp should be forwarded for H323 (listen)
Ports 5000-5059 udp should be forwarded for RTP/H323
Ports 5060-5100 upd should be forwarded for SIP/H323
Ports 30000-30010 tcp should be forwarded for H245 (Netmeeting)

And if all else fails, blame the Ekiga devs.  I realize there were some changes under the hood, but *come on...it **was** working*!

It's bad enough [Bryan Lunduke makes the remark about his HP netbook working out of the box in Ubuntu 8.10 and then having sound breaking in Ubuntu 9.04]("http://lunduke.com/?p=429").  Now I just a solid dose of it myself.

Then again, breaking stuff is part of the non-LTS territory.

---

### Post by zbangash on 2009-05-23
You are absolutely right about the version 3.2 with the bug. 

I use magicjack's registrar ( username, passwrd, proxy etc) 

I was on 8.04.  Ekiga 2.x used to work fine.  I switched to 9.04 (development). ekiga didn't work. A few days later I switched back to 8.04. Bam - good ol ekiga 2.x starts working again.  

So I have to either have the hibernation / suspend issue of 8.04, or have a non-working ekiga in 9.04.   

I'd have to find ekiga 2.x and compile it for jaunty x64.

---

### Post by zbangash on 2009-05-24
Here's a brief rundown of all that I've done / seen / checked. 

1. Ekiga 3.2 has issues.  I did manage to get it to connect 3-4 times, but that's it. Painful. 
2. Ekiga 2.0.12 works great, however compiling from source isn't my cup of java.  The deb installer package has some version dependency issues too. 
3.  SJphone : installs fine.. but not usable. 
4.  Xten-xlite / xtensoftphone. installs fine.  registers with proxy but there are audio issues with Jaunty.  Also the registration drops after a minute or so.. 


**QuteCom** is available on launchpad and works perfectly for my voip setup: 

Go to [https://launchpad.net/~cavedon/+archive/qutecom]("https://launchpad.net/~cavedon/+archive/qutecom")
Add the two sources.list entries to the software sources. 
Add the OpenPGP key. 
In terminal: sudo apt-get install qutecom

---

### Post by BrainwreckedTech on 2009-05-25
> **zbangash said:**
> **QuteCom** is available on launchpad and works perfectly for my voip setup:

Dear Lord, this makes my third PPA repository now!  ;)

QuteCom doesn't work for Ekiga accounts.  At least not for me.  I think the reason being is that if you leave the proxy field blank, QuteCom assumes the SIP domain/realm to be the proxy server.  Ekiga doesn't host their own proxy server.  It might work for paid accounts which usually do have a proxy server.

Of course, jumping ship to whichever VoIP package isn't working right now isn't the ideal solution.  Devs can't fix a bug they don't know about.  If you have the patience, it's best to file a bug report, [which I've done]("https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/380091").  Doesn't mean anyone will ever contact you, though.

Who knows, though?  Ekiga is at 3.2.4, so it might be fixed if you're willing to compile from source.  The fact is, though, most Linux users don't do that.  If the Ekiga devs could get a jaunty SVN repo up for Ubuntu, or someone could post an jaunty SVN build to a Launchpad PPA, more people could test.

---

### Post by christophermluna on 2009-06-18
Nope.  I just installed Ekiga 3.2.4 from source-- a laborious process for my noobish mind-- and got it to successfully compile and install with several new libraries from source, got it to run, exact same error, plus it no longer recognizes my otherwise fully functional webcam.

---

### Post by thelaw on 2009-08-21
I'm running Hardy Kubuntu w/ Ekiga-gtkonly 2.0.12. Configured thus:


Registrar: 
sphone.vopr.vonage.net:5061
User:
1xxxxxxxxxx where the x's are my phone number
Password:
provided by vonage

When starting the program, I recieve the following:
"Error while starting the listener for the H.323 protocol"
followed by:
"Error while starting the listener for the SIP protocol"

Starting from the cmd prompt, I get (truncated):

** (ekiga-gtkonly:7253): CRITICAL **: entry_get_bool: assertion `entry->type == GM_CONF_BOOL' failed
** (ekiga-gtkonly:7253): CRITICAL **: entry_get_int: assertion `entry->type == GM_CONF_INT' failed
** (ekiga-gtkonly:7253): CRITICAL **: entry_get_string: assertion `entry->type == GM_CONF_STRING' failed
(ekiga-gtkonly:7253): GLib-CRITICAL **: g_path_is_absolute: assertion `file_name != NULL' failed

The client displays:
Registered Accounts: 0

I'm using a linksys wrtp54g with the following ports opened up:

3478 tcp/upd
5000 - 5100 tcp/upd

I have the vonage client on an XP Machine that works just fine, however, I do not take that with me on the road.

Suggestions?

---

### Post by kiridude on 2009-08-22
For more specialised help with Ekiga, I would suggest checking this [forum]("https://answers.launchpad.net/ubuntu/+source/ekiga"). Some of the guys there are Ekiga developers and can give you the help you need.

You may also want to give Twinkle a try. You can find it in Synaptic, or from their site for the latest version.

---

### Post by afrodeity on 2010-03-24
Tried installing qutecom

```

/usr/include/boost/thread/pthread/mutex.hpp:50: void boost::mutex::lock(): Assertion `!pthread_mutex_lock(&m)' failed.

```

---

### Post by afrodeity on 2010-03-24
I have ekiga 3.2.5 installed

ekiga registration failed.

I have a TP-LINK TD 8840 router. Can't make head or tail of the Ekiga wiki

Tried: ekiga -d 4 2>&1 | grep STUN

but nothing.

---

### Post by afrodeity on 2010-03-24
If I turn on debug:

```

opulating interface list
2010/03/25 00:37:08.957	  0:00.591	                       	HalManager_dbusPopulating full interface list failed - Method "getDevices" with signature "" on interface "org.freedesktop.NetworkManager" doesn't exist

2010/03/25 00:37:09.029	  0:00.663	                       	Detecting V4L2 devices
2010/03/25 00:37:09.029	  0:00.663	                       	PV4L2Plugin	detected device metadata at /sys/class/video4linux/
2010/03/25 00:37:09.073	  0:00.707	                       	PWLib	File handle high water mark set: 28 Thread unblock pipe
2010/03/25 00:37:09.073	  0:00.707	                       	PTLib	Thread high water mark set: 5
2010/03/25 00:37:09.073	  0:00.707	                       	OpalMan	Created manager.
2010/03/25 00:37:09.074	  0:00.708	                       	OpalMan	Registered endpoint with prefix pc
2010/03/25 00:37:09.074	  0:00.708	                       	OpalEP	Created endpoint: pc
2010/03/25 00:37:09.189	  0:00.823	                       	PCSS	Created PC sound system endpoint.
Players:
Default
HDA VIA VT82xx
HDA VIA VT82xx (1)
EKIGA
*.wav
/dev/dsp
Recorders:
Default
HDA VIA VT82xx
HDA VIA VT82xx (1)
EKIGA
*.wav
/dev/dsp

2010/03/25 00:37:09.189	  0:00.823	                       	OPAL	SetMediaFormatOrder()
2010/03/25 00:37:09.189	  0:00.823	                       	OPAL	SetMediaFormatMask()
2010/03/25 00:37:09.200	  0:00.833	                       	OpalMan	Registered endpoint with prefix sip
2010/03/25 00:37:09.200	  0:00.833	                       	OpalEP	Created endpoint: sip
2010/03/25 00:37:09.200	  0:00.834	                       	PWLib	File handle high water mark set: 29 PUDPSocket
2010/03/25 00:37:09.200	  0:00.834	                       	IfaceMon	Initial interface list:
127.0.0.1 [00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:01] <00-00-00-00-00-00> (lo)
41.132.105.57 <00-00-00-00-00-00> (ppp0)

2010/03/25 00:37:09.212	  0:00.846	                       	PWLib	File handle high water mark set: 30 Thread unblock pipe
2010/03/25 00:37:09.212	  0:00.846	                       	PTLib	Thread high water mark set: 6
2010/03/25 00:37:09.213	  0:00.846	                       	PWLib	File handle high water mark set: 32 Thread unblock pipe
2010/03/25 00:37:09.213	  0:00.847	Network In...0xb7438b70	IfaceMon	Started interface monitor thread.
2010/03/25 00:37:09.213	  0:00.847	Network In...0xb7438b70	PWLib	File handle high water mark set: 33 PUDPSocket
2010/03/25 00:37:09.213	  0:00.847	                       	PTLib	Thread high water mark set: 7
2010/03/25 00:37:09.213	  0:00.847	                       	OpalMan	Registered endpoint with prefix sips
2010/03/25 00:37:09.213	  0:00.847	                       	SIP	Created endpoint.
2010/03/25 00:37:09.214	  0:00.847	                       	MonSock	Created socket bundle for all interfaces.
2010/03/25 00:37:09.214	  0:00.848	                       	PWLib	File handle high water mark set: 34 PUDPSocket
2010/03/25 00:37:09.215	  0:00.848	                       	PWLib	File handle high water mark set: 35 Thread unblock pipe
2010/03/25 00:37:09.215	  0:00.849	                       	PTLib	Thread high water mark set: 8
2010/03/25 00:37:09.215	  0:00.849	                       	OpalMan	Added route "sip:.*=pc:*"
2010/03/25 00:37:09.215	  0:00.849	                       	OpalMan	Added route "pc:.*=sip:<da>"
2010/03/25 00:37:09.216	  0:00.849	                       	OpalMan	Registered endpoint with prefix h323
2010/03/25 00:37:09.216	  0:00.850	                       	OpalEP	Created endpoint: h323
2010/03/25 00:37:09.216	  0:00.850	                       	OpalMan	Registered endpoint with prefix h323s
2010/03/25 00:37:09.216	  0:00.850	                       	H323	Created endpoint.
2010/03/25 00:37:09.227	  0:00.860	                       	PWLib	File handle high water mark set: 36 PTCPSocket
2010/03/25 00:37:09.227	  0:00.861	                       	PWLib	File handle high water mark set: 38 Thread unblock pipe
2010/03/25 00:37:09.227	  0:00.861	                       	PTLib	Thread high water mark set: 9
2010/03/25 00:37:09.227	  0:00.861	                       	OpalMan	Added route "h323:.*=pc:<db>"
2010/03/25 00:37:09.227	  0:00.861	                       	OpalMan	Added route "pc:.*=h323:<da>"
2010/03/25 00:37:09.235	  0:00.869	Opal Liste...0xb7375b70	Listen	Started listening thread on tcp$*:1720
2010/03/25 00:37:09.235	  0:00.869	Opal Liste...0xb7375b70	Listen	Waiting on socket accept on tcp$*:1720
2010/03/25 00:37:09.235	  0:00.869	Opal Liste...0xb73b6b70	Listen	Started listening thread on udp$*:5060
2010/03/25 00:37:09.266	  0:00.899	                       	MediaFormat	Removing codecs SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF
2010/03/25 00:37:09.266	  0:00.900	                       	OPAL	SetMediaFormatMask(PCM-16-48kHz,PCM-16-32kHz,PCM-16-16kHz,PCM-16,G.726-16k,G.726-24k,G.726-32k,G.726-40k,GSM-06.10,GSM-AMR,LPC-10,MS-GSM,MS-IMA-ADPCM,SpeexIETFNarrow-11k,SpeexIETFNarrow-15k,SpeexIETFNarrow-18.2k,SpeexIETFNarrow-24.6k,SpeexIETFNarrow-5.95k,SpeexIETFNarrow-8k,SpeexNB,SpeexWNarrow-8k,YUV420P,RFC4175_YCbCr-4:2:0,RGB32,RGB24,RFC4175_RGB,SIP-IM,T.140,H.224/H323AnnexQ,H.224/HDLCTunneling,Linear-16-Stereo-48kHz)
2010/03/25 00:37:09.266	  0:00.900	                       	OPAL	SetMediaFormatOrder(SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF)
2010/03/25 00:37:09.306	  0:00.940	                       	MediaFormat	Removing codecs SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF
2010/03/25 00:37:09.306	  0:00.940	                       	OPAL	SetMediaFormatMask(PCM-16-48kHz,PCM-16-32kHz,PCM-16-16kHz,PCM-16,G.726-16k,G.726-24k,G.726-32k,G.726-40k,GSM-06.10,GSM-AMR,LPC-10,MS-GSM,MS-IMA-ADPCM,SpeexIETFNarrow-11k,SpeexIETFNarrow-15k,SpeexIETFNarrow-18.2k,SpeexIETFNarrow-24.6k,SpeexIETFNarrow-5.95k,SpeexIETFNarrow-8k,SpeexNB,SpeexWNarrow-8k,YUV420P,RFC4175_YCbCr-4:2:0,RGB32,RGB24,RFC4175_RGB,SIP-IM,T.140,H.224/H323AnnexQ,H.224/HDLCTunneling,Linear-16-Stereo-48kHz)
2010/03/25 00:37:09.306	  0:00.940	                       	OPAL	SetMediaFormatOrder(SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF)
2010/03/25 00:37:09.375	  0:01.008	                       	PWLib	File handle high water mark set: 40 Thread unblock pipe
2010/03/25 00:37:09.375	  0:01.008	                       	PTLib	Thread high water mark set: 10
2010/03/25 00:37:09.376	  0:01.010	StunDetector:0xb7334b70	PWLib	File handle high water mark set: 42 PUDPSocket
2010/03/25 00:37:09.547	  0:01.181	                       	VideoOutputCoreConfBridge	Updating video view
2010/03/25 00:37:09.548	  0:01.182	                       	VideoOutputCoreConfBridge	Updating zoom
2010/03/25 00:37:09.548	  0:01.182	                       	VideoOutputCoreConfBridge	Updating Video Settings
2010/03/25 00:37:09.555	  0:01.189	                       	VideoOutputCoreConfBridge	Updating Video Settings
2010/03/25 00:37:09.555	  0:01.189	                       	VideoOutputCoreConfBridge	Updating Video Settings
2010/03/25 00:37:09.555	  0:01.189	                       	VideoOutputCoreConfBridge	Updating Video Settings
2010/03/25 00:37:09.555	  0:01.189	                       	VidInputCoreConfBridge	Updating preview size and fps
2010/03/25 00:37:09.557	  0:01.190	                       	VidInputCore	Setting new preview config: 176x144/30
2010/03/25 00:37:09.559	  0:01.193	                       	VidInputCoreConfBridge	Updating preview size and fps
2010/03/25 00:37:09.559	  0:01.193	                       	VidInputCore	Setting new preview config: 176x144/30
2010/03/25 00:37:09.572	  0:01.206	                       	VidInputCoreConfBridge	Updating device
2010/03/25 00:37:09.573	  0:01.207	                       	VidInputCore	Setting device: SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.573	  0:01.207	                       	GMVideoInputManager_ptlib	Setting Device SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.573	  0:01.207	                       	VidInputCoreConfBridge	Updating device
2010/03/25 00:37:09.573	  0:01.207	                       	VidInputCore	Setting device: SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.574	  0:01.207	                       	GMVideoInputManager_ptlib	Setting Device SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.574	  0:01.207	                       	VidInputCoreConfBridge	Updating device
2010/03/25 00:37:09.574	  0:01.207	                       	VidInputCore	Setting device: SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.574	  0:01.207	                       	GMVideoInputManager_ptlib	Setting Device SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.574	  0:01.208	                       	VidInputCoreConfBridge	Updating image
2010/03/25 00:37:09.575	  0:01.209	                       	VidInputCoreConfBridge	Updating preview
2010/03/25 00:37:09.575	  0:01.209	                       	VidInputCore	Starting preview 176x144/30
2010/03/25 00:37:09.575	  0:01.209	                       	VidInputCore	Opening device with 176x144/30
2010/03/25 00:37:09.575	  0:01.209	                       	GMVideoInputManager_ptlib	Opening Device SN9C1xx PC Camera (PTLIB/V4L2)
2010/03/25 00:37:09.575	  0:01.209	                       	GMVideoInputManager_ptlib	Opening Device with 176x144/30
2010/03/25 00:37:09.575	  0:01.209	                       	Detecting V4L2 devices
2010/03/25 00:37:09.576	  0:01.209	                       	PV4L2Plugin	detected device metadata at /sys/class/video4linux/
2010/03/25 00:37:09.615	  0:01.248	                       	PVidInDev	Open()	videoFd:-1
2010/03/25 00:37:09.615	  0:01.248	                       	PVidInDev	Close()	videoFd:-1  started:0
2010/03/25 00:37:09.615	  0:01.248	                       	Detecting V4L2 devices
2010/03/25 00:37:09.615	  0:01.249	                       	PV4L2Plugin	detected device metadata at /sys/class/video4linux/
2010/03/25 00:37:09.658	  0:01.291	                       	PVidInDev	Open()	devName:/dev/video0  videoFd:-1
2010/03/25 00:37:09.659	  0:01.293	                       	VideoInputDeviceS_STD failed : Invalid argument
2010/03/25 00:37:09.659	  0:01.293	                       	PVidDev	SetColourFormatConverter success for native YUV420P
2010/03/25 00:37:09.659	  0:01.293	                       	PVidInDev	G_PARM failed (preserving frame rate may not work) : Invalid argument
2010/03/25 00:37:09.659	  0:01.293	                       	PVidInDev	unable to reset frame rate.
2010/03/25 00:37:09.660	  0:01.294	                       	PreviewManager	Starting Preview
2010/03/25 00:37:09.661	  0:01.295	                       	AudioOutputCoreConfBridge	Updating device
2010/03/25 00:37:09.661	  0:01.295	                       	AudioOutputCoreSetting device[0]: Default (PTLIB/ALSA)
2010/03/25 00:37:09.661	  0:01.295	                       	GMAudioOutputManager_ptlib	Setting Device[0] Default (PTLIB/ALSA)
2010/03/25 00:37:09.664	  0:01.297	                       	AudioOutputCoreConfBridge	Updating device
2010/03/25 00:37:09.664	  0:01.298	                       	AudioOutputCoreSetting device[1]: Default (PTLIB/ALSA)
2010/03/25 00:37:09.670	  0:01.304	                       	AudioInputCoreConfBridge	Updating device
2010/03/25 00:37:09.670	  0:01.304	                       	AudioInputCore	Setting device: Default (PTLIB/ALSA)
2010/03/25 00:37:09.670	  0:01.304	                       	GMAudioInputManager_ptlib	Setting Device Default (PTLIB/ALSA)
2010/03/25 00:37:09.904	  0:01.538	                       	Ekiga version 3.2.5
2010/03/25 00:37:09.904	  0:01.538	                       	OPAL version 3.6.4
2010/03/25 00:37:09.904	  0:01.538	                       	PTLIB version 2.6.4
2010/03/25 00:37:09.904	  0:01.538	                       	GNOME support disabled
2010/03/25 00:37:09.904	  0:01.538	                       	Accelerated rendering support enabled
2010/03/25 00:37:09.904	  0:01.538	                       	DBUS support enabled
2010/03/25 00:37:09.904	  0:01.538	                       	GConf support enabled
2010/03/25 00:37:09.904	  0:01.538	                       	ESound support disabled
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
2010/03/25 00:37:10.337	  0:01.970	GMVideoOut...0xb74bab70	GMVideoOutputManager_X	Opening VO_MODE_LOCAL display with image of 176x144
2010/03/25 00:37:10.337	  0:01.970	GMVideoOut...0xb74bab70	XVideo	Initializing XV window with 176x144 at 26,26
2010/03/25 00:37:10.373	  0:02.007	GMVideoOut...0xb74bab70	XVideo	XvQueryExtension: Version: 2 Release: 2 Request Base: 133 Event Base: 89 Error Base: 152
2010/03/25 00:37:10.374	  0:02.007	GMVideoOut...0xb74bab70	XVideo	#0, Adaptor: NV17 Video Texture, type: input | image | , ports: 32, first port:&#65533;280
2010/03/25 00:37:10.375	  0:02.008	GMVideoOut...0xb74bab70	XVideo	Encoding List for Port 280:  id=0 name=XV_IMAGE size=2046x2046 numerator=1 denominator=1
2010/03/25 00:37:10.375	  0:02.008	GMVideoOut...0xb74bab70	XVideo	Attribute List for Port 280:
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_SET_DEFAULTS
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  set
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;0
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;0
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_ITURBT_709
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;0
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_SYNC_TO_VBLANK
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;0
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_BRIGHTNESS
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;-1000
2010/03/25 00:37:10.375	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1000
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_CONTRAST
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;-1000
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1000
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_SATURATION
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.376	  0:02.009	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;-1000
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1000
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	 &#65533;name: &#65533; &#65533; &#65533; XV_HUE
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	 &#65533;flags: &#65533; &#65533;  get set
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	 &#65533;min_color: &#65533;-1000
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	 &#65533;max_color: &#65533;1000
2010/03/25 00:37:10.376	  0:02.010	GMVideoOut...0xb74bab70	XVideo	Image format list for Port 280:
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	  0x32595559 (YUY2) packed, order: YUYV
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	  0x32315659 (YV12) planar, order: YVU
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	  0x59565955 (UYVY) packed, order: UYVY
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	  0x30323449 (I420) planar, order: YUV
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	XVideo	Grabbed Port: 280
2010/03/25 00:37:10.377	  0:02.011	GMVideoOut...0xb74bab70	XVideo	Using XVideo port: 280
2010/03/25 00:37:10.392	  0:02.025	GMVideoOut...0xb74bab70	XVideo	Found visual with colordepth of 24bits per pixel
2010/03/25 00:37:10.392	  0:02.026	GMVideoOut...0xb74bab70	X11	Created Window with ID 109051906
2010/03/25 00:37:10.393	  0:02.026	GMVideoOut...0xb74bab70	XVideo	Colorkey method: NONE
2010/03/25 00:37:10.393	  0:02.027	GMVideoOut...0xb74bab70	XVideo	Vertical sync successfully activated
2010/03/25 00:37:10.393	  0:02.027	GMVideoOut...0xb74bab70	XVideo	XQueryShmExtension success
2010/03/25 00:37:10.393	  0:02.027	GMVideoOut...0xb74bab70	XVideo	Created XvImage (176x144, data size: 38016, num_planes: 3
2010/03/25 00:37:10.393	  0:02.027	GMVideoOut...0xb74bab70	XVideo	  Plane 0: pitch=176, offset=0
2010/03/25 00:37:10.393	  0:02.027	GMVideoOut...0xb74bab70	XVideo	  Plane 1: pitch=88, offset=25344
2010/03/25 00:37:10.394	  0:02.027	GMVideoOut...0xb74bab70	XVideo	  Plane 2: pitch=88, offset=31680
2010/03/25 00:37:10.396	  0:02.030	GMVideoOut...0xb74bab70	XVideo	Using SHM extension
2010/03/25 00:37:10.398	  0:02.032	GMVideoOut...0xb74bab70	X11	Unknown wm type...
2010/03/25 00:37:10.398	  0:02.032	GMVideoOut...0xb74bab70	GMVideoOutputManager_X	VO_MODE_LOCAL: Successfully opened XV Window
2010/03/25 00:37:10.398	  0:02.032	GMVideoOut...0xb74bab70	X11	Unknown X Event 19 received
2010/03/25 00:37:12.267	  0:03.901	StunDetector:0xb7334b70	PWLib	File handle high water mark set: 43 PUDPSocket
2010/03/25 00:37:12.751	  0:04.385	StunDetector:0xb7334b70	STUN	Invalid reply packet received, transaction ID does not match.
2010/03/25 00:37:14.354	  0:05.988	StunDetector:0xb7334b70	PWLib	File handle low water mark set: 42 PUDPSocket
2010/03/25 00:37:15.365	  0:06.999	StunDetector:0xb7334b70	OPAL	STUN server "stun.ekiga.net" replies Symmetric Firewall, external IP 41.132.105.57
2010/03/25 00:37:15.365	  0:06.999	StunDetector:0xb7334b70	PTLib	Destroyed thread 0x984ee70 StunDetector:0xb7334b70(id = b7334b70)
2010/03/25 00:37:16.276	  0:07.909	                       	Listen	Stopping listening thread on udp$*:5060
2010/03/25 00:37:16.276	  0:07.910	Opal Liste...0xb73b6b70	Listen	UDP read error.
2010/03/25 00:37:16.286	  0:07.920	                       	PTLib	Destroyed thread 0x987a288 Opal Listener:0xb73b6b70(id = b73b6b70)
2010/03/25 00:37:16.286	  0:07.920	                       	PWLib	File handle low water mark set: 33 PUDPSocket
2010/03/25 00:37:16.287	  0:07.920	                       	MonSock	Created socket bundle for all interfaces.
2010/03/25 00:37:16.299	  0:07.932	                       	Listen	Stopping listening thread on tcp$*:1720
2010/03/25 00:37:16.302	  0:07.936	Opal Liste...0xb73b6b70	Listen	Started listening thread on udp$*:5060
2010/03/25 00:37:16.302	  0:07.936	                       	PTLib	Destroyed thread 0x987c490 Opal Listener:0xb7375b70(id = b7375b70)
2010/03/25 00:37:16.304	  0:07.938	Opal Liste...0xb7375b70	Listen	Started listening thread on tcp$*:1720
2010/03/25 00:37:16.304	  0:07.938	Opal Liste...0xb7375b70	Listen	Waiting on socket accept on tcp$*:1720
2010/03/25 00:37:16.318	  0:07.952	  subscriber:0xb7334b70	SIP	Start REGISTER
        aor=ethnopunk@ekiga.net
  registrar=ekiga.net
    contact=
     authID=ethnopunk
      realm=
     expire=3600
    restore=30
   minRetry=0.000
   maxRetry=0.000
2010/03/25 00:37:16.322	  0:07.956	  subscriber:0xb7334b70	SIP	Changing REGISTER handler from Unavailable to Subscribing, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:37:18.029	  0:09.663	  subscriber:0xb7334b70	OpalUDP	Binding to interface: 0.0.0.0:5060
2010/03/25 00:37:18.029	  0:09.663	  subscriber:0xb7334b70	SIP	Created transport udp$86.64.162.35:5060<if=udp$*:5060>
2010/03/25 00:37:18.030	  0:09.663	  subscriber:0xb7334b70	OpalUDP	Started connect to 86.64.162.35:5060
2010/03/25 00:37:18.030	  0:09.663	  subscriber:0xb7334b70	OpalUDP	Writing to interface 0 - "41.132.105.57%ppp0"
2010/03/25 00:37:19.405	  0:11.039	  subscriber:0xb7334b70	OpalMan	Listener interfaces: associated transport=udp$*:5060
    udp$41.132.105.57:5060
2010/03/25 00:37:19.405	  0:11.039	  subscriber:0xb7334b70	SIP	Transaction created.
2010/03/25 00:37:19.415	  0:11.048	  subscriber:0xb7334b70	DNS	SRV Lookup ekiga.net service _sip._udp
2010/03/25 00:37:20.677	  0:12.310	  subscriber:0xb7334b70	SIP	No SRV record found.
2010/03/25 00:37:20.677	  0:12.310	  subscriber:0xb7334b70	SIP	Transaction remote address is udp$ekiga.net:5060
2010/03/25 00:37:20.677	  0:12.311	  subscriber:0xb7334b70	SIP	Sending PDU (516 bytes) to: rem=udp$86.64.162.35:5060,local=udp$*:5060,if=41.132.105.57%ppp0
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 41.132.105.57:5060;branch=z9hG4bK7a4c6979-0336-df11-80b2-db99cdbe5cdc;rport
User-Agent: Ekiga/3.2.5
From: <sip:ethnopunk@ekiga.net>;tag=d8779177-0336-df11-80b2-db99cdbe5cdc
Call-ID: 9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
To: <sip:ethnopunk@ekiga.net>
Contact: <sip:ethnopunk@41.132.105.57>;q=1
Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,SUBSCRIBE,NOTIFY,REFER,MESSAGE,INFO,PING
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2010/03/25 00:37:20.678	  0:12.311	  subscriber:0xb7334b70	SIP	PDU Write failed: No such file or directory
2010/03/25 00:37:20.678	  0:12.311	  subscriber:0xb7334b70	OpalUDP	Setting interface to 41.132.105.57%ppp0
2010/03/25 00:37:20.678	  0:12.312	  subscriber:0xb7334b70	SIP	Set state Terminated_TransportError for REGISTER transaction id=z9hG4bK7a4c6979-0336-df11-80b2-db99cdbe5cdc
2010/03/25 00:37:20.678	  0:12.312	  subscriber:0xb7334b70	SIP	Did not start transaction on udp$86.64.162.35:5060<if=udp$*:5060>
2010/03/25 00:37:20.679	  0:12.312	  subscriber:0xb7334b70	SIP	Changing REGISTER handler from Subscribing to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:37:20.679	  0:12.312	  subscriber:0xb7334b70	SIP	Retrying REGISTER in 30 seconds.
2010/03/25 00:37:20.679	  0:12.313	  subscriber:0xb7334b70	SIP	Changing REGISTER handler from Unavailable to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:37:20.679	  0:12.313	  subscriber:0xb7334b70	SIP	Changing REGISTER handler from Unavailable to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:37:20.679	  0:12.313	  subscriber:0xb7334b70	PTLib	Destroyed thread 0x985cf28 subscriber:0xb7334b70(id = b7334b70)
2010/03/25 00:37:20.681	  0:12.315	Opal Garbage:0xb7479b70	SIP	Transaction id=z9hG4bK7a4c6979-0336-df11-80b2-db99cdbe5cdc destroyed.

```

---

### Post by afrodeity on 2010-03-24
If I turn on debug and initiate a call:

```

To: <sip:ethnopunk@ekiga.net>
Contact: <sip:ethnopunk@41.132.105.57>;q=1
Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,SUBSCRIBE,NOTIFY,REFER,MESSAGE,INFO,PING
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2010/03/25 00:40:22.074	  3:13.708	 Housekeeper:0xb73f7b70	SIP	PDU Write failed: No such file or directory
2010/03/25 00:40:22.074	  3:13.708	 Housekeeper:0xb73f7b70	OpalUDP	Setting interface to 41.132.105.57%ppp0
2010/03/25 00:40:22.074	  3:13.708	 Housekeeper:0xb73f7b70	SIP	Set state Terminated_TransportError for REGISTER transaction id=z9hG4bK98c6e6e5-0336-df11-80b2-db99cdbe5cdc
2010/03/25 00:40:22.074	  3:13.708	 Housekeeper:0xb73f7b70	SIP	Did not start transaction on udp$86.64.162.35:5060<if=udp$*:5060>
2010/03/25 00:40:22.075	  3:13.709	 Housekeeper:0xb73f7b70	SIP	Changing REGISTER handler from Restoring to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:40:22.075	  3:13.709	 Housekeeper:0xb73f7b70	SIP	Retrying REGISTER in 30 seconds.
2010/03/25 00:40:22.075	  3:13.709	 Housekeeper:0xb73f7b70	SIP	Changing REGISTER handler from Unavailable to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:40:22.075	  3:13.709	 Housekeeper:0xb73f7b70	SIP	Changing REGISTER handler from Unavailable to Unavailable, target=sip:ethnopunk@ekiga.net, id=9e579177-0336-df11-80b2-db99cdbe5cdc@afrodeity-desktop
2010/03/25 00:40:22.075	  3:13.709	Opal Garbage:0xb7479b70	SIP	Transaction id=z9hG4bK98c6e6e5-0336-df11-80b2-db99cdbe5cdc destroyed.


```

---

### Post by afrodeity on 2010-03-25
Upgraded to Ekiga 3.2.6. I am now doing echo testing, calls are completing. Trouble hanging up though. If I press the hangup button it freezes,

---

### Post by YannickDefais on 2010-04-05
Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)

Best regards,
Yannick

---

### Post by afrodeity on 2010-04-06
Hi Yannick, I'm using your ppa. I can now make a test call, but the app freezes when I try to hangup. 

Here is the debug
[http://paste.ubuntu.com/409930/](http://paste.ubuntu.com/409930/)

Anybody see anything?

---

### Post by YannickDefais on 2010-04-06
Hi,

This is a know issue. This bug report I made seems similar:
[https://bugzilla.gnome.org/show_bug.cgi?id=593074](https://bugzilla.gnome.org/show_bug.cgi?id=593074)

You could subscribe to it and attach your debug output too.

Best regards,
Yannick

---

### Post by amicable on 2011-01-28
Hi,

I'm trying to get registration to last more than a minute or so on Ekiga. It works for a while (1-2 mins ) and then I get 'Could not register (Forbidden)' in the accounts dialogue.

It seems that changing the details on the account (eg if I try changing the timeout) allows me to get status Registered (and I can make & receive calls), but it gets unregistered again.

Am using 3.2.6

---

