---
title: "wengophone segmentation fault"
date: 2006-06-06
forum: Desktop Environments
---

### Post by CyberAngel on 2006-06-06
When I am entering my login name and password in wengophone, I am pressing OK and the program instantly crashes with a segmentation fault.

The following info is what I am getting in the console.
I am trying to run wengo on a amd64 machine.

```
~$ wengophone
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Couldn't open file: /home/cyber/.wengo/wengo.config
ScimInputContextPlugin()
QTextBrowser: no mimesource for /usr/share/wengophone/index-fr.html
PA :: Input device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)       form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Mic Capture (hw:0,1)     form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Multichannel Capture/PT Playback (hw:0,2)        form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)    form host API: ALSA
PA :: Input device found: SAA7134: SAA7134 PCM (hw:1,0)  form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)       form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Mic Capture (hw:0,1)     form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Multichannel Capture/PT Playback (hw:0,2)        form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)    form host API: ALSA
PA :: Input device found: SAA7134: SAA7134 PCM (hw:1,0)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)      form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)   form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)      form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)   form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)      form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)   form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)       form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Mic Capture (hw:0,1)     form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: Multichannel Capture/PT Playback (hw:0,2)        form host API: ALSA
PA :: Input device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)    form host API: ALSA
PA :: Input device found: SAA7134: SAA7134 PCM (hw:1,0)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)      form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)   form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)      form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)  form host API: ALSA
PA :: Output device found: Audigy 2 ZS [SB0350]: p16v (hw:0,4)   form host API: ALSA
Mute playback: 1
PresencePopupMenu::publishMyPresenceStatus()
Connect: is connected? 0
PresencePopupMenu::publishMyPresenceStatus()
Connect: is connected? 0
Couldn't open file: /home/cyber/.wengo/user.config
Couldn't open file: /home/cyber/.wengo/cyberang3l@gmail.com/callhistory/callhistory.xml
Login: SSL enabled
* About to connect() to ws.wengo.fr port 443
*   Trying 213.91.9.249... * connected
* Connected to ws.wengo.fr (213.91.9.249) port 443
* SSL connection using DHE-RSA-AES256-SHA
* Server certificate:
*        subject: /C=FR/ST=Ile de France/L=Boulogne Billancourt/O=WENGO/OU=Secure Server/CN=ws.wengo.fr/emailAddress=noc@accelance.fr
*        start date: 2004-12-14 08:50:11 GMT
*        expire date: 2009-12-13 08:50:11 GMT
*        issuer: /C=FR/ST=Ile de France/L=Boulogne Billancourt/O=WENGO/OU=Secure Server/CN=ws.wengo.fr/emailAddress=noc@accelance.fr
* SSL certificate verify result: error number 1 (18), continuing anyway.
> POST /softphone-sso/sso.php HTTP/1.1
Host: ws.wengo.fr
Accept: */*
Content-Length: 55
Content-Type: application/x-www-form-urlencoded
Expect: 100-continue

< HTTP/1.1 100 Continue
< HTTP/1.1 200 OK
< Date: Tue, 06 Jun 2006 12:02:03 GMT
< Server: Apache/2.0.46 (CentOS)
< X-Powered-By: PHP/5.1.2
< Expires: Mon, 26 Jul 1997 05:00:00 GMT
< Last-Modified: Tue, 06 Jun 2006 12:02:03 GMT
< Pragma: public
< Cache-Control: must-revalidate, post-check=0, pre-check=0
< Content-Length: 420
< Connection: close
< Content-Type: text/xml

Login: anwser received
Login: login received

set proxy port :5060
* Closing connection #0
$$ server response code : 200
HTTPTUNNEL MODE=0
CodecList: AMR-WB0
CodecList: ILBC1
CodecList: PCMA2
CodecList: PCMU3
CodecList: AMR4
CodecList: GSM5
CodecList: H2630
CodecList: MPEG41

PA :: getWaveOutDeviceId(), found output device id 0 for Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0) (Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0))

PA :: getWaveInDeviceId(), found input device id 0 for Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0) (Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0))
** Register and initialize null audio driver
Segmentation fault

```

---

### Post by henriquemaia on 2006-06-06
I have the same error too.

Anyone knows what to do?

I'm also trying to run it on my amd64 Dapper.

---

### Post by henriquemaia on 2006-06-07
Bump.

---

### Post by daahli on 2006-06-07
What version of Wengo are you using? 2.0 beta2 was released yesterday, you may want to try it.

Wengo works well here, but I'm using 32-bit Dapper.

---

### Post by henriquemaia on 2006-06-07
[quote=daahli]What version of Wengo are you using? 2.0 beta2 was released yesterday, you may want to try it.

Wengo works well here, but I'm using 32-bit Dapper.[/quote]

WengoPhone 0.99-rev4467

Installed by Automatix.

---

### Post by CyberAngel on 2006-06-08
[QUOTE=henriquemaia]WengoPhone 0.99-rev4467

Installed by Automatix.[/QUOTE]


The same for me but it has no difference even if you install it manually..

---

### Post by henriquemaia on 2006-06-08
[quote=CyberAngel]The same for me but it has no difference even if you install it manually..[/quote]

Maybe it's a good idea to start a thread on the 64bit forum to discuss this with other 64bit users. Maybe this is something specific to the 64bit version of Wengo.

---

