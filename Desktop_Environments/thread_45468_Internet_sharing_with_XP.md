---
title: "Internet sharing with XP?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by mudshark on 2005-06-30
Hi, I am sure this must be an easy task but never having done it, unsure how to proceed. I have one bux running XP home version hooked to the internet via cable modem (earthlink). I have another box which I am going to install 5.04. What I want to do is access the internet through my XP box. Can someone tell me the steps or point me to the tutorial? Thanx in advance!

---

### Post by Lunde on 2005-06-30
[QUOTE=mudshark]Hi, I am sure this must be an easy task but never having done it, unsure how to proceed. I have one bux running XP home version hooked to the internet via cable modem (earthlink). I have another box which I am going to install 5.04. What I want to do is access the internet through my XP box. Can someone tell me the steps or point me to the tutorial? Thanx in advance![/QUOTE]
 You should look up connection sharing at the Windows help, there is a good guide there.. then just connect the two boxes.

However if you want to share it from Linux, just install the Firestarter firewall and enable internet connection sharing under Preference. 

Both solutions are pretty easy.

---

### Post by mudshark on 2005-06-30
Thanks for your reply Lunde. By "Windows help" do you mean the help do you mean the help on my XP machine? Or is there a forum that contains it?

Thanks

---

### Post by jcooper on 2005-06-30
Windows ICS can be very hit and miss, and unreliable. I have always used AnalogX (free) when having to share an internet connection from an XP machine to other clients. See the details here:

[http://windowsxp.mvps.org/analogx.htm](http://windowsxp.mvps.org/analogx.htm)

---

### Post by Lunde on 2005-06-30
[QUOTE=jcooper]Windows ICS can be very hit and miss, and unreliable. I have always used AnalogX (free) when having to share an internet connection from an XP machine to other clients. See the details here:

[http://windowsxp.mvps.org/analogx.htm](http://windowsxp.mvps.org/analogx.htm)[/QUOTE]
 Yes I ment the help in your Windows. But I would suggest using Linux as the connecting box, and use it a s a firewall

---

### Post by Takis on 2005-06-30
If you can't help having to use the XP box as the connection sharing box, what you need to do is enable Internet Connection Sharing on the NIC that goes to your Linux box. This enables DHCP, DNS and (I think) WINS on your XP box - buuuuut for some reason it's not normal DHCP. If you set your Linux box to pick up a DHCP address it won't find it. However, if you hardcode an IP address into your Linux box (has to be in 192.168.0.x range, with 255.255.255.0 subnet mask and can't be 192.168.0.1. I recommend 192.168.0.2 for simplicity.) and set the DNS provider for your Linux box to 192.168.0.1, all should be well.

These are very abstract instructions because I'm not sure how good your knowledge stuff up is. If you need step-by-step, ask and I'll write some out.

Hell, maybe I should write a How-To.

---

### Post by Lunde on 2005-06-30
[QUOTE=Takis]If you can't help having to use the XP box as the connection sharing box, what you need to do is enable Internet Connection Sharing on the NIC that goes to your Linux box. This enables DHCP, DNS and (I think) WINS on your XP box - buuuuut for some reason it's not normal DHCP. If you set your Linux box to pick up a DHCP address it won't find it. However, if you hardcode an IP address into your Linux box (has to be in 192.168.0.x range, with 255.255.255.0 subnet mask and can't be 192.168.0.1. I recommend 192.168.0.2 for simplicity.) and set the DNS provider for your Linux box to 192.168.0.1, all should be well.

These are very abstract instructions because I'm not sure how good your knowledge stuff up is. If you need step-by-step, ask and I'll write some out.

Hell, maybe I should write a How-To.[/QUOTE]
 Would be very nice with a howto Takis, several people here are asking for it.

---

### Post by Havoc on 2005-07-01
I'll second that.Please write a nice HOWTO!
But, it seems someone else has done something similar already, if not in French.Check [HERE](http://ubuntuforums.org/showpost.php?p=236988&postcount=8) ... You shouldn't reinvent the wheel.

Thanks

---

### Post by pt123 on 2005-07-09
[QUOTE=Havoc]I'll second that.Please write a nice HOWTO!
But, it seems someone else has done something similar already, if not in French.Check [HERE](http://ubuntuforums.org/showpost.php?p=236988&postcount=8) ... You shouldn't reinvent the wheel.

Thanks[/QUOTE]
 I third that, coming from Mandrake which automatically sets up internet sharing, it has been hard to get it working on ubuntu

---

