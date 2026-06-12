---
title: "Restoring Firefox"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Beggar Su on 2006-09-26
Hi, new user here.

I've recently overwritten the firefox folder in /usr/lib with the mozilla version because it resolved some crashes with multimedia plugins but had problems with extensions and shortcut commands.

So I deleted the folder and tried to install ubuntu firefox from the synaptic package manager but I get this error:

E: /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb: trying to overwrite `/usr/lib/mozilla-firefox', which is also in package mozilla-acroread

Any ideas how to reinstall ubuntu firefox?

Thank you.

---

### Post by pay on 2006-09-27
You could force it with```
sudo dpkg -i --force-all /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
```but thats not the best option. Any other ideas anyone?

---

### Post by Beggar Su on 2006-09-27
thanks that solved the problem installing ubuntu firefox.

I've got another problem when updating/installing extensions. I get the following message:

Firefox could not install the file at:
<website address>
because unexpected installation error
review javascript console log for details


javascript console says:

Error: [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFile.copyTo]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: file:///usr/lib/firefox/components/nsExtensionManager.js :: anonymous :: line 1149"  data: no]
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 1149


Any ideas?

Thanks for your help

---

### Post by pay on 2006-09-27
Yeah thats why I said that its not the best option to install it that way. Hopefully someone with more knowledge can help you out. Good luck.

---

### Post by Predius on 2006-09-27
Could you try removing and purging mozilla-acroread and firefox?

---

