---
title: "Running window applications"
date: 2009-02-04
forum: General Help
---

### Post by leroy1086 on 2009-02-04
Well - I am at the stage where I need to run some window applications for mt GPS.  Garmin does not have a linux version of MapSource.  What is the best way to download and run this application?  What software is the best for doing this?

Thanks,
Leroy

---

### Post by blazemore on 2009-02-04
TO GET THE UBUNTU STABLE RELEASE OF WINE

```
sudo apt-get install wine
```


TO GET THE MOST RECENT STABLE OFFICIAL VERSION OF WINE

1. ```
sudo su
```
This means that all commands run from now on will be run as the Super User (root), until you close the terminal window.


2.```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add
```
We download (wget) something called a "key" that verifies downloaded installation files. We install it. (apt-key add)


3. ```
echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list
```
echo just means display the next bit. The >> means append to the file /etc/apt/sources.list, which is a list of locations your computer uses to get software, when you ask it to.
In this case, we're using the official Wine repository, which has a more up-to-date version of Wine than the included Ubuntu repository.
We could just download the installation file from the Wine website, but the method I chose ensures Wine will be kept up-to-date.


4. ```
apt-get update
```
We refresh the list of repositories, making your computer aware of any new or updated packages


5. ```
apt-get install wine -y --force-yes
```
We install the package Wine (If it's not already installed). When the installer asks a question, we assume the answer is yes, even if yes is not the default option (You'll just have to trust me on this one!).


6. ```
apt-get upgrade -y --force-yes
```
If Wine was already installed, this command will update it to the version in the Wine repo, again, assuming Yes to all questions.

---

