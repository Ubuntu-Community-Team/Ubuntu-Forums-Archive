---
title: "setting up ISP in New Kubuntu install"
date: 2008-12-20
forum: General Help
---

### Post by rpmedina1 on 2008-12-20
I just finished installing Kubuntu on my other PC.  It is set up as a dual boot with XP.  I currently have ATT DSL service on the computer I am now writing on, and a Netzero low speed modem account.  I would like to know how to set up one or the other of these ISP's in Kubuntu.  I tried using a Netzero disk designed for PCs and another one designed for Mac OS.  Neither of them were recognized by Kubuntu as suitable for install.

It should be obvious by now that I am new to Linux and only marginally aware of internet service providers as they apply to the home user. What I do know is that access to sites for downloading programs for Kubuntu, and upgrades are not accessible to me at the moment. Thank you in advance for any help you can give.

---

### Post by dcstar on 2008-12-20
> **rpmedina1 said:**
> I just finished installing Kubuntu on my other PC.  It is set up as a dual boot with XP.  I currently have ATT DSL service on the computer I am now writing on, and a Netzero low speed modem account.  I would like to know how to set up one or the other of these ISP's in Kubuntu.  I tried using a Netzero disk designed for PCs and another one designed for Mac OS.  Neither of them were recognized by Kubuntu as suitable for install.

It should be obvious by now that I am new to Linux and only marginally aware of internet service providers as they apply to the home user. What I do know is that access to sites for downloading programs for Kubuntu, and upgrades are not accessible to me at the moment. Thank you in advance for any help you can give.

As it says on the Netzero site, they only support Linspire.

Ubuntu will work on any standard Internet connection.

---

### Post by editrix on 2008-12-20
I'm on dialup, so I can only answer for that. I assume by "low speed" you mean dialup.

You have to set up KPPP to dial the number, and Kmail to send and receive email. The easiest way, I suppose, would be to get the numbers from your Windows box and type them into the appropriate boxes in KPPP and Kmail.

If you're on Intrepid, you may not have KPPP. I think they left out dialup support in Intrepid. If that's the case, see if you have wvdial installed.

Lots of help here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

