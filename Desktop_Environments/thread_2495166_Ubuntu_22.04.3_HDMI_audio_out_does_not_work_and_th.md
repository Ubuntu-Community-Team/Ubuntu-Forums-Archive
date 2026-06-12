---
title: "Ubuntu 22.04.3 HDMI audio out does not work and the screen colors are wonky on new TV"
date: 2024-02-09
forum: Desktop Environments
---

### Post by mikealeonetti2 on 2024-02-09
Hello! First time caller, long time server user. I've been trying out Ubuntu Desktop. It's installed on this laptop that WAS working while connected to my 14 year old Samsung TV. I just bought a 65" Onn 4K TV from the Walmart and it doesn't seem to work as well.

Upon plugging it into the new Onn TV and the Ubuntu Desktop laptopt automatically detects the [FONT=monospace][COLOR=#000000]3840x2160[/COLOR][/FONT] resolution, but the sound doesn't work (through the HDMI). Any videos are also a bit laggy because it's a Celeron laptop. So I set the resolution to 1920x1080, which is what it was with my old Samsung TV to get the same performance back. When I set it to 1920x1080 the screen colors are really weird and the sound still doesn't work. If I change the resolution to anything other than the resolution at 3840x2160 30Hz the screen colors are terrible. No matter what resolutions I set the TV to, the sound doesn't work.

Any advice to fix the sound and the colors would be very welcome.

Laptop lspci is the following:

```
[FONT=monospace][COLOR=#000000]00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 06) [/COLOR]
00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 06) 
00:00.3 System peripheral: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06) 
00:02.0 VGA compatible controller: Intel Corporation GeminiLake [UHD Graphics 600] (rev 06) 
00:0e.0 Audio device: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 06) 
00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 06) 
00:13.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6) 
00:13.2 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6) 
00:15.0 USB controller: Intel Corporation Celeron/Pentium Silver Processor USB 3.0 xHCI Controller (rev 06) 
00:16.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06) 
00:16.3 Signal processing controller: Intel Corporation Device 31b2 (rev 06) 
00:17.0 Signal processing controller: Intel Corporation Device 31b4 (rev 06) 
00:17.1 Signal processing controller: Intel Corporation Device 31b6 (rev 06) 
00:1c.0 SD Host controller: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller (rev 06) 
00:1f.0 ISA bridge: Intel Corporation Celeron/Pentium Silver Processor LPC Controller (rev 06) 
00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822CE 802.11ac PCIe Wireless Network Adapter
[/FONT]
```

Ubuntu version:
```

[FONT=monospace][COLOR=#000000]Distributor ID: Ubuntu [/COLOR]
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy

[/FONT]
```

---

### Post by TheFu on 2024-02-09
Please don't post large images inline.  Attachments are preferred.  Some people pay for internet by the byte. Some people use a phone to read and respond to these posts. Be kind to them both.

Looks like an HDMI cable is under-spec to me.  Get a better, certified, 4K, HDMI cable.  They don't have to be expensive.  I've had good luck with Blue Rigger cables. I think that's the name.  Start there.

I'd also look up the exact specifications for allowed inputs to the TV - resolution, refresh rate, are the most important. Then I'd ensure exactly what they say is supported is what my GPU is outputting.

---

### Post by mikealeonetti2 on 2024-02-09
> **TheFu said:**
> Please don't post large images inline.  Attachments are preferred.  Some people pay for internet by the byte. Some people use a phone to read and respond to these posts. Be kind to them both.

Looks like an HDMI cable is under-spec to me.  Get a better, certified, 4K, HDMI cable.  They don't have to be expensive.  I've had good luck with Blue Rigger cables. I think that's the name.  Start there.

I'd also look up the exact specifications for allowed inputs to the TV - resolution, refresh rate, are the most important. Then I'd ensure exactly what they say is supported is what my GPU is outputting.

Really appreciate your response, and thanks for the tip on how to post here.

I'm using another 4k rated cable from Amazon by PowerBear. I don't think it's the cable because I have a Gentoo laptop that I use that's able to work just fine. Also, I have a gaming PC that runs Batocera that also works just fine. Same cable and with either 1920x1080 or 4k resolutions WITH sound intact.

I'll look up the TV to see the exact specifications and see what the difference is from those that work and those that don't.

---

### Post by grahammechanical on 2024-02-10
System Settings>Sound>Output device. Is the HDMI port selected? I am just stating the obvious. It is sometimes overlooked.

Regards

---

### Post by TheFu on 2024-02-11
Perhaps the laptop doesn't output the same quality of video and the cable is fringe compliant, so it works on other devices?
I'd test with the laptop plugged into power if you haven't tried that. Doubtful this matters, but it can't hurt to try.

The main reason I posted at all was because I got a new raspberry pi v5 computer and the video didn't just work with my normal connections.  It turned out that the microHDMI adapter was losing too much power in the connection to the normal HDMI cable.  With the Pi, I was able to turn up the voltage a little on the HDMI pins - it didn't work, but when a specific cable arrived, it all started working. Basically, the micro-HDMI adapter was the problem.  My video setup is a bit complex. I have a KVM switch and an HDMI matrix switch that does 4 inputs X 2 outputs too.  Initially, I removed that extra equipment from the HDMI chain between the computer and the monitor.

When it comes to testing, 
[LIST=1]
[*]simplify
[*]test, 
[*]repeat.
[/LIST]
Until the only failed component that cannot be split up remains. Then swap that last component, see it work, and start adding in the more complex aspects to the setup.

---

