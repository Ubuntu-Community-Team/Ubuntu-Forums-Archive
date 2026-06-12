---
title: "Security of free Google Drive clients"
date: 2023-06-15
forum: Desktop Environments
---

### Post by AbleTassie on 2023-06-15
Hello all,

I am switching back to Lubuntu from Windows 10 after having not using Lubuntu much in the last 5 years or so. A relative gave me an older PC that works well, but only has 8GB of RAM (better than my previous 4GB of RAM), so I don't want to use the Windows 10 in a Virtual Machine until I add more RAM. So I am presently dual booting Windows 10 and Lubuntu and I really want to use Lubuntu, not Windows.

For better or worse, I signed up for a $30 per year 200GB Google Drive Account (I think they raised the price $10 from when I signed up about a year ago). And I think I have about another year's subscription (automatic renewal, I think).  But now I discover that there is no Google Drive App for Linux, but I want to be able to Sync folders I am using in Lubuntu to Google Drive as I have been doing in Windows 10. I have looked at some of the threads on this topic on the Forum here and I see that there are Google Drive Clients that work with Linux. Here is an article on this topic that has been referred to in some of the posts here: [13 Best Google Drive Clients for Linux in 2022]("https://linuxhint.com/best_google_drive_clients_linux/") and here is another article specifically on Rclone and some others  [How To Mount Google Drive Locally As Virtual File System In Linux]("https://ostechnix.com/how-to-mount-google-drive-locally-as-virtual-file-system-in-linux/") . Here is another more recent article: [ 9 Best Google Drive Clients for Linux in 2023]("https://www.tecmint.com/google-drive-clients-linux/") .

Some of these are free, some have a GUI and others use Terminal Commands. I would prefer a free Drive Client that uses a GUI, not Terminal Commands and that syncs local files just like the Google Drive App does on Windows. I'd be willing to consider a Drive Client that uses Terminal Commands, however: Rclone looks like it might be a candidate in this regard. Maybe I'm unrealistic and too much of a typical consumer, but that's what I am thinking. 

But my main question at this point relates to security. Given the fact that the information in Google Drive may be pretty confidential, I am concerned about any security vulnerabilities that are added by a Drive Client.

QUESTION(S): Do you think one or more of the free Drive Clients add significant security vulnerabilities? 

Are there one or more of the free Drive Clients that you think are better in terms of security?

Any other comments anybody has on free Google Drive Clients for Linux that allow syncing of local files like the Google Drive App does will be welcomed.

Thank you,

A.

---

### Post by AbleTassie on 2023-06-15
> **AbleTassie said:**
>  now I discover that there is no Google Drive App for Linux, but I want to be able to Sync folders I am using in Lubuntu to Google Drive as I have been doing in Windows 10. I have looked at some of the threads on this topic on the Forum here and I see that there are Google Drive Clients that work with Linux. Here is an article on this topic that has been referred to in some of the posts here: [13 Best Google Drive Clients for Linux in 2022]("https://linuxhint.com/best_google_drive_clients_linux/") and here is another article specifically on Rclone and some others  [How To Mount Google Drive Locally As Virtual File System In Linux]("https://ostechnix.com/how-to-mount-google-drive-locally-as-virtual-file-system-in-linux/") . Here is another more recent article: [ 9 Best Google Drive Clients for Linux in 2023]("https://www.tecmint.com/google-drive-clients-linux/") .

Some of these are free, some have a GUI and others use Terminal Commands. I would prefer a free Drive Client that uses a GUI, not Terminal Commands and that syncs local files just like the Google Drive App does on Windows. I'd be willing to consider a Drive Client that uses Terminal Commands, however: Rclone looks like it might be a candidate in this regard. Maybe I'm unrealistic and too much of a typical consumer, but that's what I am thinking. 

Any other comments anybody has on free Google Drive Clients for Linux that allow syncing of local files like the Google Drive App does will be welcomed.

Thank you,

A.

I figured that since Rclone is in the Repos, it is probably secure. So I went ahead and installed it. I also was able to mount my entire GoogleDrive with Rclone using a Terminal Command, _**I think**_ -- I had to abort the mounting as it was taking too long: I have about 150 GB on GoogleDrive. I really want to just mount individual GoogleDrive Folders/Directories with Rclone and I was also able to do this using Terminal Commands. But there is a big problem: working with individual files on my PC in the mounted folders is very slow. It takes a long time to open PDF files and it takes a long time to save pdf files if I make any changes. I cannot open Open Document Files at all by clicking on the icons in the local drive folder. I can get them to open by opening the Libre Office Writer, stipulating odt documents and then going to the odt document in the local drive folder. But I cannot save any changes I make to Open Office Documents. This may be because Libre Office Writer is timing out. 

So it appears that slowness is a major problem I am having with Rclone. This may be because I followed the default instructions for installing Rclone in the article [How To Mount Google Drive Locally As Virtual File System In Linux]("https://ostechnix.com/how-to-mount-google-drive-locally-as-virtual-file-system-in-linux/") . Similar default instructions are on the Rclone website. There is some special number that you can use to identify yourself or your drive and that may have slowed down the process. But given the fact that the article is not that old (**Last Updated on** January 31, 2023) it's hard to believe that that would make such a big difference. If I can't improve on Rclone, I will have to try something else.

Any comments from anybody will be welcomed.

Thanks,

A.

P.S. My understanding of "mounting" is that the mounted Folder is essentially as if it were on a usb thumbdrive (although the connection would be slower than an thumbdrive). But maybe I have this wrong. In any case, when I modify files using the GoogleDrive App in Windows, the processes are very fast even though the connection from the PC to GoogleDrive is via the internet. So the internet connection speed cannot be the sole explanation for the problem I am having.

---

### Post by TheFu on 2023-06-16
If you care about security, don't use cloudy services.

Cloudy services put your data on someone else's drive, inside someone else's computer, inside someone else's building, at the end of someone else's network.  At least you are paying, but I doubt that matters to google at all.  Does your contract with them claim they won't mine your data at all or look at it in any way except to provide necessary access for you?  If not, assume they are using your data just like they use everyone else's data ... and are selling it somehow.  

Nearly all cloudy services do this and most ISPs too.

If you aren't paying for a service, you are definitely the product being sold.  OTOH, do you believe that Google who sells everyone's data has a special way they deal with only paid customer data storage?  I don't.

The only way I'd use cloudy services for data storage would be if I encrypted all the data outside any program tied to the remote system.  There are a number of programs that claim they encrypt data just before it is transmitted to cloud storage.  I don't buy it.

Of course, some people say I'm overly paranoid.

---

### Post by AbleTassie on 2023-06-19
> **TheFu said:**
> If you care about security, don't use cloudy services.

Cloudy services put your data on someone else's drive, inside someone else's computer, inside someone else's building, at the end of someone else's network.  At least you are paying, but I doubt that matters to google at all.  Does your contract with them claim they won't mine your data at all or look at it in any way except to provide necessary access for you?  If not, assume they are using your data just like they use everyone else's data ... and are selling it somehow.  

Nearly all cloudy services do this and most ISPs too.

If you aren't paying for a service, you are definitely the product being sold.  OTOH, do you believe that Google who sells everyone's data has a special way they deal with only paid customer data storage?  I don't.

The only way I'd use cloudy services for data storage would be if I encrypted all the data outside any program tied to the remote system.  There are a number of programs that claim they encrypt data just before it is transmitted to cloud storage.  I don't buy it.

Of course, some people say I'm overly paranoid.

Thanks Fu,

You make a lot of good points and I think that paranoia is often justified. And people often find it particularly justified in retrospect. I am reminded of a small sign over a desk at a place I used to work that said: *"Just because you're paranoid, doesn't mean they're not out to get you."* 

QUESTION(S): 

How do you back up your data? 

If you do it on a peripheral hard drive, are you concerned that something (e.g., an accident) might render the hard drive inaccessible?

If you do use a cloud service, do you encrypt the data yourself before uploading to the cloud service?

AN UPDATE ON MY ORIGINAL POST:

I have managed to get Rclone working to some extent, I have downloaded a test folder directly from Google Drive, mounted the downloaded test folder in Google Drive using Rclone, worked on an Open Office test Document in the test folder, and then copied the downloaded test folder (with changes to the test document)  to the Rclone drive folder. The Rclone drive folder will ask if you want to overwrite the original folder & documents. I reply, "yes," and the changed test folder and test document appear in Google Drive.   

But there are some problems: I can mount the entire drive or a folder/directory within the drive, but once mounted I cannot unmount the mounted drive or folder if it is not empty. I have checked and other people have had similar problems and I am not sure if or what the solutions to this problem are. So, it's not like having a Google Drive App that works with Ubuntu.

Any more comments from any body else will be welcomed.

Thanks,

R.

---

### Post by TheFu on 2023-06-20
> **AbleTassie said:**
>  
QUESTION(S): 

How do you back up your data? 


I've posted 50+ times how to do backups in these forums. Just last week, I posted a link to a presentation I gave at a local LUG on the topic.

> **AbleTassie said:**
>  
If you do it on a peripheral hard drive, are you concerned that something (e.g., an accident) might render the hard drive inaccessible?

My backups are a little more complex than that.  However, I don't try to protect against 3 failures, just 2.

> **AbleTassie said:**
>  
If you do use a cloud service, do you encrypt the data yourself before uploading to the cloud service?

I avoid using all cloud services.  A buddy in another state and I swapped HDDs with our initial backups on them, then trickle change data between our local backups and the remote storage overnight. This is for the 3rd copy of the data.  I follow the 3-2-1 backup method.

I don't trust google to do anything that isn't in their interest.  I'd really like it if they started requiring payment to access all their services and blocked them to people who don't pay. Then I'd 100% know they weren't stealing my data. As it is today, I block much of google on the internet, but because it is "free". Lots of others choose, ignorantly, to make use of those free aspects and give our data away.  I'll never understand why people would use google DNS - it it like giving some one a list of domains you are visiting for free and they can use it anyway they like.  And don't get me started about gmail users.  Sigh.

---

### Post by BBQdave on 2023-06-20
> **AbleTassie said:**
> I signed up for a $30 per year 200GB Google Drive Account (I think they raised the price $10 from when I signed up about a year ago). And I think I have about another year's subscription (automatic renewal, I think).  But now I discover that there is no Google Drive App for Linux...

I install Google Chrome on GNU/Linux machines and there is no issue accessing Google Drive, I access through Chrome. And Google Chrome Settings allow you to sync files and folders, even work off line.

I have never installed the Google Drive specific application (button) because I did not find it necessary. If Google Drive application button was installed, it would just be another path to Google Drive. As in, click the button or click the tab in Chrome.

My case use with Google Chrome, was a home school group. It was nice to coordinate, share files and work with others who were on different OS's :)

As far as security, Google assures users that they are not data mining your Google Drive or Gmail, instead gain information from your searches. Given that, I still treat Google as public space.

If you wish your data private, I would recommend a portable drive such as USB drive. Years back, I upgraded my laptop HD to an SSD. I took the laptop HD and put it in an USB case, portable private data storage :)

---

### Post by AbleTassie on 2023-06-21
Thank you Fu and BBQ Dave,

Your replies are food for thought.

**BBQ Dave, you said:** *"And Google Chrome Settings allow you to sync files and folders, even work off line."* In the settings I have on the Google Chrome webbrowser, there is a way to change the settings to work offline. But I don't see any way to change the settings to allow syncing of files or folders *_on my PC to Google Drive_*. Can you please elaborate further?

Thank you,

A.

---

### Post by Tadaen_Sylvermane on 2023-06-22
> I don't trust google to do anything that isn't in their interest.  I'd  really like it if they started requiring payment to access all their  services and blocked them to people who don't pay. Then I'd 100% know  they weren't stealing my data. As it is today, I block much of google on  the internet, but because it is "free". Lots of others choose,  ignorantly, to make use of those free aspects and give our data away.   I'll never understand why people would use google DNS - it it like  giving some one a list of domains you are visiting for free and they can  use it anyway they like.  And don't get me started about gmail users.   Sigh.

I do these things because I don't give a damn what they do with my search history. While many may have a reason for that type of security there is little point to going overboard from my perspective. I find it odd though. I'm normally paranoid about things but internet services don't seem to trigger me like most other things. I can't explain it. It's not ignorance. It's a choice. Many like myself are perfectly happy to give something up for the convenience. To each their own.

---

### Post by TheFu on 2023-06-22
> **Tadaen_Sylvermane said:**
> I do these things because I don't give a damn what they do with my search history. While many may have a reason for that type of security there is little point to going overboard from my perspective. I find it odd though. I'm normally paranoid about things but internet services don't seem to trigger me like most other things. I can't explain it. It's not ignorance. It's a choice. Many like myself are perfectly happy to give something up for the convenience. To each their own.

Once you've had your data stolen and used against you, you'll likely change your stance.  But at that point, it will be too late.  I've had stolen data-related issues 3 times in my life, before I cared about security AND privacy.  My stance is that it is none of their business what I do or where I visit.  

The default, legally, should be that they cannot take that data without positive approval AND paying the people who's data they take, even a token amount + free services.  That token amount would probably make it too much trouble, so they'd find a different business model.  
Why isn't that default?  I don't know.  
If someone takes my photo and starts running an advertisement without my approval, I can sue them.  Why can't we sue all the tech companies for stealing much more sensitive data than just a photo?

Just because you aren't worried, that doesn't impact my desire to be for everyone else and myself.  I really dislike that I have no control over what happens and which systems are used for some data.  If I could, I'd have all my health care data only on paper, never stored in any computer, unless completely randomized, disconnected from insurance and name and location information.

There are laws that protect who we call (via POTS phones) and what we watch on CATV that are stronger than any internet protections.  Seems odd that is the case. Our representatives aren't protecting the right things nearly enough.  The US has the worst privacy laws ... because representatives will be slammed by big-tech if they ever do implement reasonable privacy as the default for everyone.  Sadly, the US market is large enough so that other countries that do have better privacy laws will either be dropped or run at a loss with money still being earned in the US stealing our data.

---

### Post by AbleTassie on 2023-06-30
Thanks to everybody for their thoughts on this thread that I started. I think there is significant good information in this thread.

Thanks,

Able

---

