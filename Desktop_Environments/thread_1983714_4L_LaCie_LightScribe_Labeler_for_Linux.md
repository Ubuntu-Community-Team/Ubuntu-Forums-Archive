---
title: "4L: LaCie LightScribe Labeler for Linux"
date: 2012-05-20
forum: Desktop Environments
---

### Post by Mia1990 on 2012-05-20
I knew how to do this at one time but i guess i forgot i have a lightscribe dvd burner and i have lacie lightscribe labeler for linux installed i remember how to start it but what i want to do is add it to the menu or dash. I'M using ubuntu 12.04. Can somebody help me?

---

### Post by Virus692 on 2012-05-28
this is what you seek.

[http://ubuntuforums.org/showthread.php?t=512742](http://ubuntuforums.org/showthread.php?t=512742)

First download "Lightscribe System Software" and "Lightscribe Simple Labeler" from [www.lightscribe.com]("http://www.lightscribe.com") .

Now, System -> Administration -> Users and Groups, and make a  group "wheel" and add any users that you want to be able to use the  Lightscribe software to this group.
Or in a terminal:

     
     ```
sudo addgroup wheel sudo adduser username wheel 
```where username is the name of the user you want to add to this group.

```
 Install alien, libpng3 and libqt3-mt through Synaptic, or in a terminal:
``````
      sudo aptitude install alien libpng3 libqt3-mt 
```Now in a terminal, cd to the directory where you saved the lightscribe software and issue the following command:

     
     ```
sudo alien -i --scripts lightscribe-1.8.13.1-linux-2.6-intel.rpm 
```
It will quit complaing about it's license file... To solve:

     
     ```
sudo gunzip /usr/share/doc/lightscribeLicense.rtf.gz 
```Now again

     
     ```
sudo alien -i --scripts lightscribe-1.8.13.1-linux-2.6-intel.rpm 
```And it should finish its installation without trouble...

Time to install the Labeler software:

     
     ```
sudo alien -i lightScribeSimpleLabeler-1.4.128.1-linux-2.6-intel.rpm 
```Everything should now be installed under /opt/lightscribeApplications/ . To do a test run of Simple Labeler: 

     
     ```
cd  /opt/lightscribeApplications/SimpleLabeler/ ./SimpleLabeler 
```If it does't work, the output given here should point you in the  right direction to fix it ( or post here ). I get some X errors, but  they don't seem to do any harm.

You also should install Lacie Lightscribe Labeler frome here: [http://www.lacie.com/support/drivers...r.htm?id=10094]("http://www.lacie.com/support/drivers/driver.htm?id=10094") . This will give you some options Simple Labeler hasn't. In a terminal, cd to the directory where you dowloaded it and:

     
```
       sudo alien -i 4L-1.0-r6.i586.rpm 
```To do a test run:

     ```

     4L-gui
```

---

