---
title: "Connecting Nokia 6230i to Ubuntu with Gammu"
date: 2009-05-20
forum: General Help
---

### Post by alexlittle on 2009-05-20
Hi,

I'm attempting to use Gammu to connect my Nokia 6230i to my Asus EeePC (running Jaunty), via a CA53 cable (not bluetooth/IR), but I keep running into the error "No response in specified timeout. Probably phone not connected." every time I run 'gammu --identify'. The phone is connected (!), every time I plug in the phone the 'new mobile broadband connection' wizard appears, and I have been able to connect using KMobileTools but that doesn't do everything I'd like - which is why I'd like to use gammu. So I'm assuming the problem isn't with the cable.

I've seen quite a few other forum messages etc with similar problems although none seem to give me a satisfactory solution. I've checked that the user has access to /dev/ttyACM0, that the pin code is turned off on the phone, and many of the other suggestions, but none of these work for me.

I don't even know if the problem lies with the phone/asus/ubuntu/gammu! The gammuru and the gammulog are shown below. Please let me know if any other info would be useful.
Many thanks in advance to anyone who can help me out with this :-)

Cheers,
Alex 

-----
gammuru:
[gammu]
synchronizetime = no
name = mymobile
connection = dku2
logfile = gammulog
logformat = textall
model = 6230i
port = /dev/ttyACM0



-----
gammulog:
[Gammu            - 1.22.1 built 17:44:42 Dec 22 2008 using GCC 4.3]
[Connection       - "dku2"]
[Connection index - 0]
[Model type       - "6230i"]
[Device           - "/dev/ttyACM0"]
[Runing on        - Linux, kernel 2.6.28-11-generic (#43~lp349314apw5 SMP Tue Apr 21 17:26:20 UTC 2009)]
[Module           - "1100|1100a|1100b|1200|2600|2610|2630|2650|2760|3100|3100b|3105|3108|3109c|3200|3200a|3205|3220|3300|3510|3510i|3530|3589i|3590|3595|5000|5100|5140|5140i|5200|5300|5310|6020|6021|6030|6060|6070|6085|6086|6100|6101|6103|6111|6125|6131|6151|6170|6200|6220|6230|6230i|6233|6234|6270|6280|6300|6310|6310i|6385|6500c|6500s|6510|6610|6610i|6800|6810|6820|6822|7200|7210|7250|7250i|7260|7270|7360|7370|7600|7900|8310|8390|8800|8910|8910i"]
SENDING frametype 0x10/length 0x0C/12
00 |01 |00 |10 |07 |01 |02 |06 |0A |14 |17 |399                 ...........9    
Getting model
SENDING frametype 0xD1/length 0x05/5
00 |01 |00 |03 |00                                              .....           
[ERROR: incorrect char - 00, not 0c]
[ERROR: incorrect char - 0c, not 14]
[ERROR: incorrect char - 10, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 0c, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 01, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 10, not 14]
[ERROR: incorrect char - 07, not 14]
[ERROR: incorrect char - 01, not 14]
[ERROR: incorrect char - 02, not 14]
[ERROR: incorrect char - 06, not 14]
[ERROR: incorrect char - 0a, not 14]
[ERROR: incorrect char - 14, not 14]
[ERROR: incorrect char - 17, not 14]
[ERROR: incorrect char - 39, not 14]
[ERROR: incorrect char - 00, not 0c]
[ERROR: incorrect char - 0c, not 14]
[ERROR: incorrect char - d1, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 05, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 01, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 03, not 14]
[ERROR: incorrect char - 00, not 14]
[Retrying 1 type 0xD1]
SENDING frametype 0xD1/length 0x05/5
00 |01 |00 |03 |00                                              .....           
[ERROR: incorrect char - 00, not 0c]
[ERROR: incorrect char - 0c, not 14]
[ERROR: incorrect char - d1, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 05, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 01, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 03, not 14]
[ERROR: incorrect char - 00, not 14]
[Retrying 2 type 0xD1]
SENDING frametype 0xD1/length 0x05/5
00 |01 |00 |03 |00                                              .....           
[ERROR: incorrect char - 00, not 0c]
[ERROR: incorrect char - 0c, not 14]
[ERROR: incorrect char - d1, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 05, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 01, not 14]
[ERROR: incorrect char - 00, not 14]
[ERROR: incorrect char - 03, not 14]
[ERROR: incorrect char - 00, not 14]
Init: Phone->GetModel failed with error TIMEOUT[14]: No response in specified timeout. Probably phone not connected.
[Terminating]
[Closing]

---

