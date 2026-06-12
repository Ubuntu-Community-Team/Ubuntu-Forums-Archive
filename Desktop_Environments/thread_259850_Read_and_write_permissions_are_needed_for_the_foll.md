---
title: "Read and write permissions are needed for the following file"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Red Knuckles on 2006-09-17
In newly installed versions of Firefox and Swiftfox 1.5.0.6 after I installed my extensions I get the following error:

Read and write permissions are needed for the following file:
/home/zzzzz/.mozilla/firefox/a5rwtprq.default/forecastfox/profiles.xml

How do I get rid of this? The operating system is newly installed Kubuntu 6.06. I've checked some of this forum as well as firefox, swiftfox, and Kubuntu forums and did several forum searches but haven't found anything yet.:confused:

---

### Post by skierkegaard on 2006-09-17
sudo chmod a+rw /home/zzzzz/.mozilla/firefox/a5rwtprq.default/forecastfox/profiles.xml

---

### Post by Red Knuckles on 2006-09-18
> **Red Knuckles said:**
> In newly installed versions of Firefox and Swiftfox 1.5.0.6 after I installed my extensions I get the following error:

Read and write permissions are needed for the following file:
/home/zzzzz/.mozilla/firefox/a5rwtprq.default/forecastfox/profiles.xml

How do I get rid of this? The operating system is newly installed Kubuntu 6.06. I've checked some of this forum as well as firefox, swiftfox, and Kubuntu forums and did several forum searches but haven't found anything yet.:confused:

Thanks skierkegaard I was actually looking in my Fedora Manual for specifics on how to change permissions when I got your post. That worked, problem solved. :biggrin:

---

### Post by Red Knuckles on 2006-09-18
For training and education purposes would:

sudo chmod 640 /home/zzzzz/.mozilla/firefox/a5rwtprq.default/forecastfox/profiles.xml 

Also work? I need a better resource as a reference for changing permissions than what I found in my Fedora manual.

---

