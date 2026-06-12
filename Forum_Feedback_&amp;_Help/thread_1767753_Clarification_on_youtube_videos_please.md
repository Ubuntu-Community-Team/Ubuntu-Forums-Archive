---
title: "Clarification on youtube videos please"
date: 2011-05-26
forum: Forum Feedback &amp; Help
---

### Post by nothingspecial on 2011-05-26
The question regarding where youtube videos are stored when you watch them and how to find them keeps coming up.

Would you rather I didn't post how to find them?

reference

[http://ubuntuforums.org/showpost.php?p=10859519&postcount=3](http://ubuntuforums.org/showpost.php?p=10859519&postcount=3)


Thankyou.

---

### Post by lisati on 2011-05-26
This is an area which requires us to tread carefully. According to the Youtube [terms of service]("http://www.youtube.com/static?gl=US&template=terms"):

_Section 4A:_
> You agree not to distribute in any medium any part of the Service or the Content without YouTube's prior written authorization, unless YouTube makes available the means for such distribution through functionality offered by the Service (such as the Embeddable Player).

_Section 5B:_
> Content is provided to you AS IS. You may access Content for your information and personal use solely as intended through the provided functionality of the Service and as permitted under these Terms of Service. You shall not download any Content unless you see a “download” or similar link displayed by YouTube on the Service for that Content. You shall not copy, reproduce, distribute, transmit, broadcast, display, sell, license, or otherwise exploit any Content for any other purposes without the prior written consent of YouTube or the respective licensors of the Content. YouTube and its licensors reserve all rights not expressly granted in and to the Service and the Content.

---

### Post by nothingspecial on 2011-05-26
Thanks for the reply. That's kind of why I asked. The command line gobbldygook I posted just finds where in the file system the video is stored. However, armed with that information, someone could easily copy the video. 

The whole point of firefox and flash doing this is so that users cannot just copy them from /tmp like they used to.

So I'm asking, next time I see a post asking where the temp flash files are stored, do I

Show them how to find them, which answers the question (but also provides a way for them to copy the videos) And mention the fact that you are not supposed to.

Or should I just not post it.

---

### Post by lovinglinux on 2011-05-26
I am not a lawyer, but my vision on the subject is that if you do not intent to download for long term storage or distribution, but solely to deal with system limitations, for instance because flash uses too much CPU and if you play the video locally it works great, then I think it should be considered fair use.

That is the only reason I have included such functionality in one of my extensions, which is designed to deal with such performance issues.

One thing to consider is that Mozilla has business relations with Google and they do not prohibit download helper extensions in AMO site. In fact, there are tons of add-ons that allow to download videos from YouTube. So the question is, do Google really care? Is Mozilla being against the law by hosting those extensions? I doubt it.

If they were so worried about someone copying the videos they would implement real time streaming protocol that wouldn't save any temp file.

As long as you access YouTube page, Google will probably ignore what you are doing. However, if you use some application that completely bypass YouTube, then Google will probably take action like it did, if I am not mistaken, with Totem.

---

### Post by mips on 2011-05-26
> **lisati said:**
> This is an area which requires us to tread carefully. According to the Youtube [terms of service]("http://www.youtube.com/static?gl=US&template=terms"):


When Google has their own browser and then makes available on their own webstore extensions to download youtube videos, convert youtube videos to other formats or extract the audio from videos to mp3 one has to assume they are allowing you to download this content from their own site. Surely if they did not allow this they would not make the extensions available on their own webstore for their own browser? Why would they violate their own terms of service?

In their terms of service they harp on distribution. This implies downloading the content and then passing it one to another party. Which brings me to linking and embedding which would not be considered distribution as you are not downloading anything, you are merely posting a link to the content on their site and keep in mind they gladly provide you with that link in two different formats. If they did not want you linking and embedding they would not provide you with those to link options for pasting on other sites.

As for the flv files that end up on your hard drive I would deem this to fall under the category of personal use as described by youtube. They choose flash knowing full well the files end up on your HDD, you cannot hold the user responsible for this. If they did not want this they would have implemented some form of DRM via streeming etc.

I really consider this a non-issue in all honesty.

---

### Post by lovinglinux on 2011-05-26
> **mips said:**
> When Google has their own browser and then makes available on their own webstore extensions to download youtube videos, convert youtube videos to other formats or extract the audio from videos to mp3 one has to assume they are allowing you to download this content from their own site. Surely if they did not allow this they would not make the extensions available on their own webstore for their own browser? Why would they violate their own terms of service?

I forgot that Chrome also has video download add-ons :-)

---

### Post by nothingspecial on 2011-05-26
> **mips said:**
> 


I really consider this a non-issue in all honesty.

I'm not asking weather one should or should not do whatever they like with the videos that youtube place within your system when clicking the play button.

I'm asking what the forums position is on showing people where they are.

I have a function in my .bashrc that uses youtube-dl to download a video and pipe it through mplayer without saving it to my hard disk. Having read the replies to my op it seems that the function is violating youtube's ToS.

Weather or not I continue to use it is my business. Weather or not I should post it on Ubuntu Forums is my question.

---

### Post by ivanovnegro on 2011-05-26
> **lovinglinux said:**
> I am not a lawyer, but my vision on the subject is that if you do not intent to download for long term storage or distribution, but solely to deal with system limitations, for instance because flash uses too much CPU and if you play the video locally it works great, then I think it should be considered fair use.

That is the only reason I have included such functionality in one of my extensions, which is designed to deal with such performance issues.

One thing to consider is that Mozilla has business relations with Google and they do not prohibit download helper extensions in AMO site. In fact, there are tons of add-ons that allow to download videos from YouTube. So the question is, do Google really care? Is Mozilla being against the law by hosting those extensions? I doubt it.

If they were so worried about someone copying the videos they would implement real time streaming protocol that wouldn't save any temp file.

As long as you access YouTube page, Google will probably ignore what you are doing. However, if you use some application that completely bypass YouTube, then Google will probably take action like it did, if I am not mistaken, with Totem.

Thanks for clarifying this, it was also my opinion about that.
I saw some threads closed of the mods asking things about Youtube videos, this one is still open. I know about the Code of Conduct, its just a grey zone regarding stored or downloaded videos.

---

### Post by ivanovnegro on 2011-05-26
> **nothingspecial said:**
> I'm not asking weather one should or should not do whatever they like with the videos that youtube place within your system when clicking the play button.

I'm asking what the forums position is on showing people where they are.

I have a function in my .bashrc that uses youtube-dl to download a video and pipe it through mplayer without saving it to my hard disk. Having read the replies to my op it seems that the function is violating youtube's ToS.

Weather or not I continue to use it is my business. Weather or not I should post it on Ubuntu Forums is my question.

For me its also a non-issue but regard the Code of Conduct, if I read it right, you should not post it. The mods have to correct me if I am wrong.

---

### Post by mips on 2011-05-26
> **nothingspecial said:**
> I'm not asking weather one should or should not do whatever they like with the videos that youtube place within your system when clicking the play button.

I'm asking what the forums position is on showing people where they are.

Does it really matter whether they are located on your HDD or in RAM? It's all a form of memory that belongs to you.

You say they don't want you copying the files to HDD but why do they allow you to use their Chrome browser with extensions from their webstore to do exactly that? Whether you do it your way or use their extensions the end result is the same, files on your hard drive.

So whether I post a guide here on how to install extensions in your browser and click a button to download the video from youtube (which they will allow without issue I reckon) or I tell them how to dump it from RAM instead to achieve exactly the same thing is no different in my eyes as you still end up with the files on your HDD.

---

