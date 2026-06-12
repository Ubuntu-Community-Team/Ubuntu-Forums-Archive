---
title: "Installing gyachi on ubuntu 11.04"
date: 2011-04-05
forum: Desktop Environments
---

### Post by reptilezone2002 on 2011-04-05
[B]just copy & past the lines it worked i tested on 11.04 beta 1 
[/B]


**Step 2:** Use the *Display sources.list* entries drop-down box to select the version of Ubuntu you're using. 
  **Step 3:** You'll see that the text-box directly below reads something like this:

 
  [FONT=&quot]deb [http://ppa.launchpad.net/adilson/experimental/ubuntu](http://ppa.launchpad.net/adilson/experimental/ubuntu) maverick main [/FONT]
  [FONT=&quot]deb-src [http://ppa.launchpad.net/adilson/experimental/ubuntu](http://ppa.launchpad.net/adilson/experimental/ubuntu) maverick main [/FONT]
   
  Copy those lines. 
  **Step 4:** Open a terminal and type: 
  sudo gedit /etc/apt/sources.list

 
  This will open a text editor containing the list of archives that your system is currently using. Scroll to the bottom of the file and paste the lines you copied in the step above. 
  Save the file and exit the text editor. 



  **Step 5:** Back on the PPA's overview page, look for the *Signing key* heading. You'll see something like: 



  [1024R/27B81625]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x50AB22E78528C1C33363EE08D715961D27B81625&op=index")



  Copy the portion after the slash but not including the help link; e.g. just 27B81625 . 
  **Step 6:** Now you need to add that key to your system so Ubuntu can verify the packages from the PPA. In your terminal, enter:.


  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 27B81625

 
  This will now pull down the PPA's key and add it to your system. 



  **Step 7:** Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added: 



  sudo apt-get update

 
  sudo apt-get install gyachi

---

### Post by gg234 on 2011-04-07
Try this PPA [http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)

---

### Post by reptilezone2002 on 2011-04-07
**Adilson has build the package for 11.04 & i tried it its working .. great**

[https://launchpad.net/~adilson/+archive/experimental?field.series_filter=](https://launchpad.net/~adilson/+archive/experimental?field.series_filter=)

sudo add-apt-repository [B]ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi


[/B]

---

