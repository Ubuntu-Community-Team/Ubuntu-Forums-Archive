---
title: "Thunderbird and system proxy settings"
date: 2009-03-24
forum: Desktop Environments
---

### Post by BkkBonanza on 2009-03-24
I've tried all sorts of ways to make Thunderbird use the system proxy settings and just can't get it to work. 

Here's what I'm doing and what I've tried.

I'm using a socks 5 proxy created by ssh. It works fine with Thunderbird if you manually set the socks proxy values. And it works fine with other programs. Firefox is awesome - it picks up the system set values when you choose "use system". Great. 

But I don't want to edit every program's proxy values every time I change my connections and have various proxy settings. When I change it once in System->Preferences->Network Proxy I'd like it to be used by Thunderbird.

Apparently System->Preferences->Network Proxy should set the environment variables for the proxy - but it appears not to. I trid various options for Thunderbird including the Add-On "Environmental Proxy", and also altering the config.use_system_prefs to true. None of this works. It seems no matter what Thunderbird will not use the system set values.

Has anybody out there done this or found a solution? I'd love to know.
I'd also love to know why System->Preferences->Network Proxy doesn't set the environment. I checked it in a console and they aren't there.

Cheers for your help.

---

### Post by onyxwolf on 2009-09-23
Yeah me too!!! I've been using evolution (Ugly and Novell). Switched to Thunderbird because of that, but the final straw was that the Mail Notification volume wouldn't stick when using the per application volume in PulseAudio volume control. But now this! tried environment proxy but it doesn't help. Maybe a work around is to use environment proxy and a script to set those and one to change them back? (grabbing at straws now)

---

