---
title: "We need to talk about the wireless troubleshooting script"
date: 2024-08-24
forum: Forum Feedback &amp; Help
---

### Post by currentshaft on 2024-08-24
i

---

### Post by jeremy31 on 2024-08-26
I guess I can get rid of that info.  This is because of changes in netplan and Ubuntu 24.04, once tested I  can push my changes.  When I use the script normally, I see permissions errors for netplan results in the script and I wonder if some people are running as root

---

### Post by currentshaft on 2024-08-27
.

---

### Post by jeremy31 on 2024-08-28
If you are running 24.04, try it now```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info
sudo ./wireless-info
```
Then look at the results

The script wasn't meant for users to run with sudo as sudo is in the script itself only when needed.  When run normally the script asks for the password but it isn't used for the netplan parts

---

### Post by currentshaft on 2024-08-30
I ran the script: it provided no output and then asked for my sudo password without an explanation. I Control-C'd a few of those prompts and it still produced a result. We should indicate why a password is being requested.

I'm not sure exactly how the SSID names and especially a list of all nearby networks helps troubleshooting, but if possible we should redact them: they are a big privacy risk.

The rest looks clean. Thanks for working on this.

---

