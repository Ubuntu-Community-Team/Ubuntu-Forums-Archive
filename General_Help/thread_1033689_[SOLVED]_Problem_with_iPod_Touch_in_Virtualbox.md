---
title: "[SOLVED] Problem with iPod Touch in Virtualbox"
date: 2009-01-07
forum: General Help
---

### Post by Ketara on 2009-01-07
I recently got an iPod Touch from a friend, and have been trying to get it to sync in Windows XP through Virtualbox, since iTunes won't work in Hardy.

I have all of that working fine. It took a while to get Virtualbox to read the USB port, but after a half a day I have iTunes reading the iPod. I sync'd apps and pictures so I know it's working properly.

However, I want to keep all of my friends music in addition to adding all of mine. The standard way to do that is to open up the iPod in My Computer and transfer the music files to iTunes like it was an external drive, and then sync normally.

This is where we get to my problem.

Although iTunes will read the iPod in virtualbox and it will sync it in virtualbox, I cannot get the iPod to show up in My Computer, meaning I cannot transfer files in any sort of non iTunes related fashion. Essentially, iTunes is seeing the thing but nothing else in Windows is seeing it.

Any ideas?

---

### Post by mattytee on 2009-01-08
In iTunes, with the iPod connected, see if you have an "enable disk use" option. Tick that option and you should be able to do what you're wanting to do. 

What did you do to get the USB working?

---

### Post by sendblink23 on 2009-01-08
> **mattytee said:**
> In iTunes, with the iPod connected, see if you have an "enable disk use" option. Tick that option and you should be able to do what you're wanting to do. 

What did you do to get the USB working?

"enable disk use"   What??   never in my Life  have I ever seen that on any Apple iTouch or Apple iPhone, in itunes or in any Computer??  hello this is not a regular iPod

Are you sure you haven't drank anything today?

Well if i'm wrong.. well.. damn.. ok maybe I'm drunk.. but i have never seen that option ever for itouch's or iphones.. when connected to any computer

---

### Post by sendblink23 on 2009-01-08
If you want to access INSIDE the ipod touch  (to get access inside its internal files)...   the only way is...  by a Jail broken ipod (through  Cydia installing OpenSSh)  and afterwards in Linux (ubuntu)  ..  clicking on Places  / Network  .. and if yoru Wireless is on (inside yoru iTouch)  .. your  Apple iTouch  is suppose to appear in the Network list there   ..

the login is:  root
password is: apline


if it is not jailbroken.. that Apple iTouch .. then there isn't any other way to access inside that apple itouch. 


you probably have to get on a regular Windows or  Mac to be able to work that through itunes normally.



> **Ketara said:**
> I recently got an iPod Touch from a friend, and have been trying to get it to sync in Windows XP through Virtualbox, since iTunes won't work in Hardy.

I have all of that working fine. It took a while to get Virtualbox to read the USB port, but after a half a day I have iTunes reading the iPod. I sync'd apps and pictures so I know it's working properly.

However, I want to keep all of my friends music in addition to adding all of mine. The standard way to do that is to open up the iPod in My Computer and transfer the music files to iTunes like it was an external drive, and then sync normally.

This is where we get to my problem.

Although iTunes will read the iPod in virtualbox and it will sync it in virtualbox, I cannot get the iPod to show up in My Computer, meaning I cannot transfer files in any sort of non iTunes related fashion. Essentially, iTunes is seeing the thing but nothing else in Windows is seeing it.

Any ideas?

---

### Post by Ketara on 2009-01-08
> **mattytee said:**
> In iTunes, with the iPod connected, see if you have an "enable disk use" option. Tick that option and you should be able to do what you're wanting to do. 

What did you do to get the USB working?

I do not see an enable disk use option. Additionally, while I was at work today I hooked the thing up to one of the office computers. Their versions of XP read the touch, although they read it as a camera. (a seperate hurdle I'll tackle later) Virtualbox won't read the thing at all, although it works perfectly in iTunes. This is really confusing me.

[http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy) got the USB ports working for me beautifully, although it took me a couple hours to do, because I forgot that the TinyXP image file I have is on a data partition that wasn't mounted after I restarted. I ran around going "WHY ISN'T IT WORKING NOW" and reinstalling **** till I realized I just had to mount the drive. Was funny.

I can get virtualbox to read all of my other USB appliances normally. Thumbdrive and HD enclosure both work fine.

---

### Post by sendblink23 on 2009-01-08
Did you read my POST ...  I replied to the really wrong  suggestion that person mentioned.. THE IS NO  "ENABLE DISK USE"  for Apple iTouch & Apple iPhones.. it is not a regular ipod


Just follow what I mentioned on my Next Post ... but if it is not  Jailbroken..

then you can't really do anything...   just only head into a regular Windows or mac  computer, to access itunes correctly)

---

### Post by Ocxic on 2009-01-08
iPod touch does not work with ubuntu unless you jailbreak it, and use GTK-pod or imilar program, there is a bug the prevents it from working w/ virtualbox, though i have heard of people having success with VMWare, so you might want to try that.

---

### Post by sendblink23 on 2009-01-08
> **Ocxic said:**
> iPod touch does not work with ubuntu unless you jailbreak it, and use GTK-pod or imilar program, there is a bug the prevents it from working w/ virtualbox, though i have heard of people having success with VMWare, so you might want to try that.



let's hope.. he has a 1st generation Apple iTouch   :P

if its  2nd genaration he's skrewed

---

### Post by Ketara on 2009-01-08
The touch works 100% fine in virtualbox with iTunes, just not with anything else. I will put out a screenshot, since apparently I am confusing people. I am not trying to get it to do anything through Ubuntu because I know that won't work, just through virtualbox.

[http://i59.photobucket.com/albums/g311/saviourforce/soyuz/Screenshot-6.png](http://i59.photobucket.com/albums/g311/saviourforce/soyuz/Screenshot-6.png)

It is a 2nd gen itouch. One of the new ones with the speaker n' shiz.

I can try VMware, but am hesitant. I hear it's a bit of a pain compared to virtualbox.

---

### Post by sendblink23 on 2009-01-08
We repeatedly mentioned it... THIS IS NOT A REGULAR *iPOD*

YOU WILL NOT BE ABLE TO SEE IT ON  **MY COMPUTER**

Like I said 2 times already


Anyways  you have a 2nd Generation iPod.. then you will not be able to access inside the Apple iTouch   .. (Only 1st generation ipods are able to do that..  since they can be Jail Broken.. IN WHICH.. it makes the Possibility to Access inside the IPOD, but through a WIFI...  SCP  access.. trick     in Cydia  downloading  OpenSSH)


in other words.. no you will not be able to do what you are asking for...  probably in 1 or 2 months  until I HOPE.. that they finally  manage to Jailbrake  2nd generation Apple iTouchs  (so far for now.. its  Impossible)  ..  so  no Access  inside  the ipod internal Hard Drive .. till then



> **Ketara said:**
> The touch works 100% fine in virtualbox with iTunes, just not with anything else. I will put out a screenshot, since apparently I am confusing people. I am not trying to get it to do anything through Ubuntu because I know that won't work, just through virtualbox.

[http://i59.photobucket.com/albums/g311/saviourforce/soyuz/Screenshot-6.png](http://i59.photobucket.com/albums/g311/saviourforce/soyuz/Screenshot-6.png)

It is a 2nd gen itouch. One of the new ones with the speaker n' shiz.

I can try VMware, but am hesitant. I hear it's a bit of a pain compared to virtualbox.

---

### Post by sendblink23 on 2009-01-08
Just for you to be certain.. of any of my answers

I own:

2 Apple iPhones (1st gen & 3G Apple iPhone)  both jailbroken
2 Apple iTouch's (1st gen *Jailbroken* & 2nd Gen *STOCK till Jailbrake is created in the future*)


So I completely Know everything there is abotu iPhones & iTouch's

---

### Post by Ketara on 2009-01-08
After some thorough interwebs searching, I have found a solution.

[http://i-funbox.com/](http://i-funbox.com/) Worked surprisingly well.

[http://img.photobucket.com/albums/v606/Roybea/Screenshot-8.png](http://img.photobucket.com/albums/v606/Roybea/Screenshot-8.png)

Thanks anyway everybody, eheh.

---

### Post by sendblink23 on 2009-01-08
> **Ketara said:**
> After some thorough interwebs searching, I have found a solution.

[http://i-funbox.com/](http://i-funbox.com/) Worked surprisingly well.

[http://img.photobucket.com/albums/v606/Roybea/Screenshot-8.png](http://img.photobucket.com/albums/v606/Roybea/Screenshot-8.png)

Thanks anyway everybody, eheh.



I actually  saw that  before...  but didn't tested it


Anyways good for that *news ..  I hope pretty soon, 2nd Gen iTouch gets to Jailbrake.. and then you would be able to Make WONDERS with it  (like get all AppStore Apps for Free, Any iTunes song for Free.. customize the whole look of it...  a whole allot more) 

hehee  anyways  Thanx for that

---

### Post by Braddigan on 2009-01-08
> **sendblink23 said:**
> 
Anyways good for that *news ..  I hope pretty soon, 2nd Gen iTouch gets to Jailbrake.. and then you would be able to Make WONDERS with it  (like get all AppStore Apps for Free, Any iTunes song for Free.. customize the whole look of it...  a whole allot more) 


I'm fairly sure you shouldn't refer to pirating as a 'wonder' never the less a 'WONDER.'  Now we know why you're a proud owner of so many jailbroken phones.

---

### Post by mahasmb on 2009-01-08
Hey there, Dan.

What are you doing around these here parts?

Ketara, mark the thread as solved. (click Thread Tools > Solved near the top of the page)

---

