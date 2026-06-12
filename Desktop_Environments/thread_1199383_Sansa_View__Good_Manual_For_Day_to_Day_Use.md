---
title: "Sansa View : Good Manual For Day to Day Use"
date: 2009-06-28
forum: Desktop Environments
---

### Post by ckonestroh on 2009-06-28
Sansa View 

   [COLOR="DarkOrchid"]**Pro's**[/COLOR]-  16 gigs, Sd Card Micro, Its own software (Microsoft &$%$$%$#$@)
           Uses Both MTP and MSC (Autodetect)....

    **[COLOR="Red"] Cons[/COLOR]**-  MSC(Autodetect), Freezes, overheats, No real software support for linux (Company doesn't support linux), and 
            Movie Formats.....


 Mtp or Media Transport Protocol has nothing to do with mp3 player Freezing..


[I][SIZE="3"]
**Sansa View has poor documentation**[/SIZE][/I]...

1. [COLOR="Red"]**Freezes**[/COLOR]
[COLOR="Blue"]
Solution[/COLOR] Put Sansa View into lock mode and unlock device seems to skip songs Do this several times to get it to unfreeze...

Also makes sure none of the buttons are mashed down.. If all else fails turn it off and on again....

2. [COLOR="Red"]Heat Problem[/COLOR]

[COLOR="Blue"]Solution[/COLOR] Don't hold Sansa View for more then 1 Minute is my rule or you will cause the Sansa to overheat... Your body heat plus disk spinning bad idea... Will kill drive...

3. [COLOR="Red"]**Static Electricity**[/COLOR]
[COLOR="Blue"]
Solution [/COLOR]buy plastic case similar to Ipod's to reduce static build up when in your pocket this should also stop overheating and buttons from becoming stuck...



                                 **[COLOR="Blue"][COLOR="Blue"]Work Arounds-[/COLOR][/COLOR]** 


1. MSC - A removable storage device that automatically selects a communication protocol to exchange information with a host computer includes a physical layer interface... 

 [COLOR="DarkOrchid"] Pro's[/COLOR] - Music, Videos, and Photos arranged in Alphabetical order....
          Easy to use plug and play...

  [COLOR="Red"]Con's[/COLOR] - Only Recognizes 2.1 to 3.1 gigs of storage, problem displaying 
           media that exceeds more the half the storage available... 


2.** MTP** - Media Transfer Protocol 

   **[COLOR="Purple"]Pro's[/COLOR]**- Sees all 16 gigs, Easy folder browsing...

   [COLOR="Red"]**Con's**[/COLOR] - Limited Alphabetical order, Bit confusing....

   Access [COLOR="Navy"]**MTP PUT DEVICE IN LOCK MODE + LEFT ARROW...WAIT TILL DEVICE SCREEN FLASHES ONCE WAIT AGAIN IT WILL FLASH AGAIN... PLUG DEVICE IN YOUR NOW IN MANUAL MODE.....**
[/COLOR]
                               [SIZE="4"][COLOR="Purple"]MTP VS MSC[/COLOR][/SIZE]


  MTP does do Alphabetical order ,but limits it to you having to select Artist with wheel... Ok ,but I personally Like to just select  Play all and have it list both artist and song....


  MSC puts files in folders and does a great Alphabetical sorting....


MTP for ubuntu and linux is the way to go with devices set to be fully user friendly under windows....

[SIZE="3"]**[COLOR="Blue"]Xtra's[/COLOR]**[/SIZE]


 [COLOR="Green"][SIZE="3"]**Screen Protector**[/SIZE][/COLOR] [SIZE="4"][COLOR="Indigo"]**Must Have!**[/COLOR][/SIZE]
Cases  [http://www.anvsoft.com/eshop/category.php?category_id=547]("http://www.anvsoft.com/eshop/category.php?category_id=547")

Cheap only 5 bucks + shipping and handling...

Headphones Personal choice lots of different types lock for ones with Noise canceling... There going to run anywhere from  $50 to upto $300 or more....

My personnel pick is  [SIZE="3"]**Boss $179 bucks**[/SIZE],[SIZE="3"] **iFrogz Ear Pollution $30(for the Kids)**[/SIZE] , [SIZE="3"]**Skullcandy Sk Pro $150**[/SIZE] and [SIZE="3"]**Sennheiser HD-25 $130**[/SIZE]....
[COLOR="SeaGreen"][SIZE="4"]
You get what you pay for when it comes to Headphones[/SIZE][/COLOR]... Most of the Reliable and Great Sound are not going to be found in stores..... They want to sell cheap and breakable ones so you go out and buy more....






Go over Software Usage Next Post...

---

### Post by ckonestroh on 2009-06-29
Software is in a bit of a bind with none being able to preform libmtp right out the box....


Good News is developers are testing libmtp .0.3.7 making improvements to mtp protocol for file recognition..... From lists, album covers, Artist etc....


When Ubuntu will release it as a stable package is to be seen...

Not sure on status for autodetect/MSC....?

Right now with Jaunty you would have to edit device lines in code... In order to get device to work with current players....

---

### Post by ckonestroh on 2009-07-06
More Good news --

 [SIZE="4"]**.is_audio_player**[/SIZE] add this file to your Sansa it will then be possible to see Sansa View via any player I like both Amarok and Rhythmbox for this....


Haven't tried to add files through either music program.... I just open the folder in MTP and add music..

Info .is_audio_player file is done through Hal to access device via players not through MTP 

do search on google to find more info...

Good Luck

---

### Post by ckonestroh on 2009-07-26
Sansa Video Conversion:

Linux WinFF :            Windows Any Video Converter:

Video Settings:

Container (file extension) .Mp4
Frame Size: 320x240
Frame Rate: 30FPS
Video: 384 or 512


Audio Settings:

Audio Codec: aac
Audio: 128/192kbps (up to you really)
Sample: 44100
Audio Bitrate: 64
Audio Channels:2

Tip most Ipod .mp4 will not play in Sansa View becuase the usually call for a Frame Size of : 640 X 480 which is beyond the view resolution in Sansa View .... Sansa View will say format not supported....



WinFF can also convert from wma to mp3 files to listen in Linux/Ubuntu

Remember some wma to mp3 will not be possible not all wma codecs in linux support all times of wma media from windows...

---

### Post by Sciamano on 2009-11-02
> **ckonestroh said:**
> Tip most Ipod .mp4 will not play in Sansa View becuase the usually call for a Frame Size of : 640 X 480 which is beyond the view resolution in Sansa View .... Sansa View will say format not supported....

The 640x480 resolution actually is not the reason why the View will not play the files.
[It has been found out]("http://www.anythingbutipod.com/forum/showthread.php?t=22476") that the following resolutions all work on the Sansa View. If a file does not play, it's probably a format problem, not a resolution one.
Thanks for suggesting WinFF though, I will try that!

Here is the list of supported resolutions:
    * 176x144 * (found by Member vrg3)
    * 320x172 * (found by Member vrg3)
    * 320x240
    * 368x208
    * 400x240
    * 480x272
    * 512x384
    * 544x400
    * 576x240
    * 576x304
    * 576x320
    * 608x464
    * 624x336
    * 624x352
    * 640x256
    * 640x272
    * 640x320
    * 640x336
    * 640x352
    * 640x368
    * 640x384
    * 640x400
    * 640x480 - 4:3

---

### Post by TheElite1x721987 on 2010-01-24
> **ckonestroh said:**
> Sansa View 

   [COLOR="DarkOrchid"]**Pro's**[/COLOR]-  16 gigs, Sd Card Micro, Its own software (Microsoft &$%$$%$#$@)
           Uses Both MTP and MSC (Autodetect)....

    **[COLOR="Red"] Cons[/COLOR]**-  MSC(Autodetect), Freezes, overheats, No real software support for linux (Company doesn't support linux), and 
            Movie Formats.....


 Mtp or Media Transport Protocol has nothing to do with mp3 player Freezing..


[I][SIZE="3"]
**Sansa View has poor documentation**[/SIZE][/I]...

1. [COLOR="Red"]**Freezes**[/COLOR]
[COLOR="Blue"]
Solution[/COLOR] Put Sansa View into lock mode and unlock device seems to skip songs Do this several times to get it to unfreeze...

Also makes sure none of the buttons are mashed down.. If all else fails turn it off and on again....

2. [COLOR="Red"]Heat Problem[/COLOR]

[COLOR="Blue"]Solution[/COLOR] Don't hold Sansa View for more then 1 Minute is my rule or you will cause the Sansa to overheat... Your body heat plus disk spinning bad idea... Will kill drive...

3. [COLOR="Red"]**Static Electricity**[/COLOR]
[COLOR="Blue"]
Solution [/COLOR]buy plastic case similar to Ipod's to reduce static build up when in your pocket this should also stop overheating and buttons from becoming stuck...



                                 **[COLOR="Blue"][COLOR="Blue"]Work Arounds-[/COLOR][/COLOR]** 


1. MSC - A removable storage device that automatically selects a communication protocol to exchange information with a host computer includes a physical layer interface... 

 [COLOR="DarkOrchid"] Pro's[/COLOR] - Music, Videos, and Photos arranged in Alphabetical order....
          Easy to use plug and play...

  [COLOR="Red"]Con's[/COLOR] - Only Recognizes 2.1 to 3.1 gigs of storage, problem displaying 
           media that exceeds more the half the storage available... 


2.** MTP** - Media Transfer Protocol 

   **[COLOR="Purple"]Pro's[/COLOR]**- Sees all 16 gigs, Easy folder browsing...

   [COLOR="Red"]**Con's**[/COLOR] - Limited Alphabetical order, Bit confusing....

   Access [COLOR="Navy"]**MTP PUT DEVICE IN LOCK MODE + LEFT ARROW...WAIT TILL DEVICE SCREEN FLASHES ONCE WAIT AGAIN IT WILL FLASH AGAIN... PLUG DEVICE IN YOUR NOW IN MANUAL MODE.....**
[/COLOR]
                               [SIZE="4"][COLOR="Purple"]MTP VS MSC[/COLOR][/SIZE]


  MTP does do Alphabetical order ,but limits it to you having to select Artist with wheel... Ok ,but I personally Like to just select  Play all and have it list both artist and song....


  MSC puts files in folders and does a great Alphabetical sorting....


MTP for ubuntu and linux is the way to go with devices set to be fully user friendly under windows....

[SIZE="3"]**[COLOR="Blue"]Xtra's[/COLOR]**[/SIZE]


 [COLOR="Green"][SIZE="3"]**Screen Protector**[/SIZE][/COLOR] [SIZE="4"][COLOR="Indigo"]**Must Have!**[/COLOR][/SIZE]
Cases  [http://www.anvsoft.com/eshop/category.php?category_id=547]("http://www.anvsoft.com/eshop/category.php?category_id=547")

Cheap only 5 bucks + shipping and handling...

Headphones Personal choice lots of different types lock for ones with Noise canceling... There going to run anywhere from  $50 to upto $300 or more....

My personnel pick is  [SIZE="3"]**Boss $179 bucks**[/SIZE],[SIZE="3"] **iFrogz Ear Pollution $30(for the Kids)**[/SIZE] , [SIZE="3"]**Skullcandy Sk Pro $150**[/SIZE] and [SIZE="3"]**Sennheiser HD-25 $130**[/SIZE]....
[COLOR="SeaGreen"][SIZE="4"]
You get what you pay for when it comes to Headphones[/SIZE][/COLOR]... Most of the Reliable and Great Sound are not going to be found in stores..... They want to sell cheap and breakable ones so you go out and buy more....






Go over Software Usage Next Post...

Upgrade to latest firmware to fix the overheating issue.

And what disk spinning? The Sansa View is a flash based player. There is no hard drive at all, only flash memory. 

The latest firmware will also solve the majority of the freezing as well. As for a plastic case for static....you don't need it. I've owned a Sansa View for over 2 years now (16gig) its been in my pocket many many times. Never had issues with static, heat, or even scratches. It's a very rugged device.

---

### Post by epidemiks on 2010-02-02
this helped me a lot:

[http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html](http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html)

---

