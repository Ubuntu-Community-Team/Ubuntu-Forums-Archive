---
title: "[SOLVED] What app to use for Yahoo Messenger?"
date: 2007-05-29
forum: Desktop Environments
---

### Post by siddartha on 2007-05-29
Hello,

My experience overall is poor. The oficial linux client is zero. You can just forget you know there is such an executable. The windows client is written up so badly that each version broke somthing on the Windows stations I have used on the way. And it is non-standard enough that wine reports it as broken. And there is the flashing spam you get along with the oficial client.

The free alternatives I know are kopete for KDE and gaim for Gnome. Kopete is a nice thing. Last time I have checked it was missing some functions like 'log in as invisible' and multiple profiles suppot. Besides that it was working quite well.

On the other hand with Gnome we have gaim.. and that is a problem. I am trying to do my best to keep a gnome environment and not mix up different toolkits, but this is becoming a nuisance. Is there a choice besides Gaim?

I mean gaim is a nice project and it got Sean Egan a nice job and a book and a site where he puts his face on and says 'hurray, we have another beta, the 10th'. That's about it. And something is terribly wrong with this app. After all this years they are still unable to have multiple identities with yahoo messenger. And this feature is broken so bad is almost unusable - you can log in as the other identity but all identities will be set up as online and people can write to any of those but you will write them only with the one you logged in making the idea useless. It is getting worse as you started a talk with somebody with ID1 and logged later on with ID2 you will have two windows for the same talk and if you are trying to write in the first window something funny would have happen.

So far there is no audio or video support but they made sure you have the silly check mail function. Also the yahoo module can't tunnel through http making this useless for proxy environments. The MSN module can do that but I guess the two teams do not collaborate. From what I recall over they years this project would have died long ago if it wasn't for trillian guys to share the knowledge of how to circumvent the limits put in place by the various IM networks to force people use their own official client.

Again jabber would be a better protocol or so I heard but as long as most of my friends are on yahoo I should join them. And I have problems with sending and receiving files, with the fact that there is no multimedia support (but they do have a toaster plug in, hurray!). Do I have any other alternative?

Cheers,
Sidd

---

### Post by jrusso2 on 2007-05-29
There is one other choice its called Gyach Improved Check out this link for more information

[http://ubuntuforums.org/showthread.php?t=190900](http://ubuntuforums.org/showthread.php?t=190900)

---

### Post by jtnoob on 2007-06-01
I am currently using GyachI, but I can't voice chat with a friend of mine who is using the latest yahoo. When we first connect, his yahoo says I am running an outdated version of yahoo. Am I missing updates to GyachI?

Thanks

---

### Post by CityofAsh on 2007-06-01
I dont believe there are any Gyachi updates as of yet.  Hopefully soon tho. I need to get yahoo voice chat working.

---

### Post by hank hill on 2007-06-01
yes i need yahoo phone in & out ,that is what i use instead of a landline because it is CHEAP and quality is good .I mean 1 cent out for anywhere in usa is good & 3.00 a month for calls in ,u just can't beet it.
fortuantly i have another machine next to this one running xp . But i'd much rather use my yahoo phone on linux,if there is a way plz tell me.

thx for starting this thread & my use of it .......

---

### Post by loell on 2007-06-01
gyachi voice chat is meant for room voice chat.

for voice call

 [URL="http://http://ubuntuforums.org/showthread.php?t=414121"]   	
HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service. [/URL]

---

### Post by ivesjd on 2007-06-01
can always try meebo.com

---

### Post by grathinam on 2007-06-02
any ideas how to make yahoo voice chat work, I do use Gaim, it is good but It seems it does not support voice, is there a way to make this work.

I did looked  at [http://wwwl.meebo.com/](http://wwwl.meebo.com/), it is nice, but I don't see a way to make voice chat work.

any suggestions would be really appreciated.

Thanks in advance

---

### Post by mihailfontul on 2007-06-04
Hi,

You need chat, audio and video, right?
So, for audio / video you can try gizmoproject, but there is a luck of chat in this application (at least for YAHOO).
On the other hand you have openwengo, with full support for chat / audio / video. The application is still beta, so can be unstable.

mihailfontul

---

### Post by grathinam on 2007-06-04
yeap will try openwengo, thanks for your help on this

---

### Post by siddartha on 2007-06-06
Gyachi works pretty well for me. The interface might seem a bit weird at the beginning but there's nothing to worry about as you will learn it pretty fast. In case you are like me only with yahoo accounts it is by far a better alternative to gaim.

---

### Post by loell on 2007-06-06
you can also try gyachi-sidetrack a sub-fork of gyachi that adresses the interface. :)

[GyachI-Sidetrack (yahoo messenger , webcam , voice chat)]("http://ubuntuforums.org/showthread.php?t=431290&highlight=gyachi")

---

### Post by siddartha on 2007-06-06
To my surprise it seems that I am using the sidetrack. What are the main differences between all those gyach forks?

---

### Post by loell on 2007-06-06
protocol wise , mostly none , the difference are fixes and developer maintainership.

say the first three years, developer A is available, but the next three years developer A becomes busy, so developer B assumes development under a new name for three years, again developer B becomes unavailable
so developer C comes in under a new name again and maitains the code base ;)

with regards to my fork (sidetrack) , is more of a proposal/testing to the main.

---

### Post by miggl on 2007-06-06
Also, have you tried the new GAIM, now renamed Pidgin? They may have addressed the issue of multiple identities.

---

### Post by siddartha on 2007-06-12
I tried on Windows Gaim Beta6  and it is waaay behind gyach*

I would also avoid Gaim as the development team is more interested with fame rather the actual aplication. Some bugs and feature requests were closed just like that with the notice 'the might be solved in the CVS' when they prepared the 2.0. Various beta appeared and they are almost ready to release the final version yet the problems haven't been addressed. Reopening the same requests lead to closing them again because of the move to anoter site. Well, I sure hope they took notes as I won't bother to do this each time they think they got a new interface.

There is still no video and audo support and Egan was more than egar to please google as to get a job there. There is nothing wrong with that action. I admire him for that - it proves that open source does bring money to the programmers. In the end gaim-vv was dropped, the video update never came and that's the final result. The only thing noticeable in the YM area was the fact that they finally were able to put the option to log in as invisible. And there are oh so many features of YM that Gaim won't have soon unless there will be another guy working for them. I mean sharng photos, voice, telephony, going through the proxy by embedding the actual conversation in HTTP commands, etc. This happened already several times when various IM networks blocked access for the unofficial clients connecting and the trillian team helped them out.

---

### Post by grathinam on 2007-06-14
am having challenges installing this, is there a document or write up someplace which I can use to install the same (Gyachi)


thanks in advance

---

### Post by siddartha on 2007-10-16
Solved the problem: dumped gaim, pidgin or whatever they'd wish to call  it 3 years from now. If you need more than just Yahoo - go for kopete as it has almost the same functionality and than some more.

As for yahoo, gyache sidetrack is working excellent. And it knows most of the things it should know (video for example) and also some nice tricks like show who logs in invisible and so on.

---

### Post by ampload on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: voice bug in gyachi-e using ubuntu 7.10   .deb [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can get into my Yahoo Chat Room easly! ..but when I "click" on for Voice I get this error message? ..&#8220;Cannot run gyvoice due to the following missing files:   tsd32.dll  and  tssoft.acm  

Not in the following directories: 
      /usr/lib/win32/ 
      /usr/local/lib/win32/       how can I fix this problem ??
]
I installed ..  gyachi_1.1.0-1_i386_gusty.deb

is there a add on patch or plugin for voice/sound in gyachi (yahoo)? or where can i download tsd32.dll .. tssoft.acm ?

btw Im running Ubuntu 7.10  .deb  gnome

------------------------------------------------------------------------------
Wow " loell" your brilliant that "codac pack "( gyachi_codac's.deb )
 
That did the trick perfectly thank you so much my friend  :-)
                                      ((( Solved )))

---

### Post by XVII on 2007-12-01
I use pidgin for everything.

---

### Post by loell on 2007-12-01
> **ampload said:**
> **This post could be related to an Ubuntu bug filed at**: voice bug in gyachi-e using ubuntu 7.10   .deb [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can get into my Yahoo Chat Room easly! ..but when I "click" on for Voice I get this error message? ..“Cannot run gyvoice due to the following missing files:   tsd32.dll  and  tssoft.acm  

Not in the following directories: 
      /usr/lib/win32/ 
      /usr/local/lib/win32/       how can I fix this problem ??
]
I installed ..  gyachi_1.1.0-1_i386_gusty.deb

is there a add on patch or plugin for voice/sound in gyachi (yahoo)? or where can i download tsd32.dll .. tssoft.acm ?
 
                                                                                     thanks in advance :)
btw Im running Ubuntu 7.10  .deb  gnome

you need to install [gyachi-codecs.deb]("http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb?use_mirror=jaist")

---

### Post by bharadwaj on 2007-12-02
why aren't you trying the yahoo messenger for linux

[http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)

---

### Post by loell on 2007-12-02
> **bharadwaj said:**
> why aren't you trying the yahoo messenger for linux

[http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)

have you tried it? ;) 

cause it doesn't work for almost a century now.

---

### Post by siddartha on 2007-12-07
> **XVII said:**
> I use pidgin for everything.

Great! I guess all could benefit from few hints of how to open a video connection via yahoo, how to have a voice chat over yahoo, or skype anyway. Did they solve the problem with yahoo over http?

Cheers,
Sidd

---

### Post by siddartha on 2007-12-07
> **bharadwaj said:**
> why aren't you trying the yahoo messenger for linux

[http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)

It's one of the few apps that is behind gaim or whatever they would like to call it 2 years from now.

---

