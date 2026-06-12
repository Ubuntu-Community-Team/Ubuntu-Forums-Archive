---
title: "ffmpeg ffserver streaming problem"
date: 2009-03-19
forum: General Help
---

### Post by d2009 on 2009-03-19
Hi, 

I am trying to stream video files using ffserver. I am able to stream audio and video for mpeg, mp3, flv, swf, rm formats properly..

But i am badly stuck with avi, 3gp, mov, mp4.. when i try to play it in the browser using [http://localhost:8096/test.avi](http://localhost:8096/test.avi), it just keeps waiting endlessly or saves a file with 0 bytes. 

My FFmpeg version SVN-r17942.. 

I am using these in my ffserver.conf file.. 

<Stream test.mov>
Feed feed1.ffm
Format mov
VideoSize 720x480
VideoFrameRate 30
AudioCodec ac3
AudioChannels 1
AudioSampleRate 48000
</Stream>

<Stream test.avi> 
Feed feed1.ffm 
Format avi
VideoFrameRate 24
Audiocodec mp2
AudioSampleRate 44100
</Stream>

<Stream test.3gp> 
Feed feed1.ffm 
Format 3gp
VideoSize 176x144 
Audiocodec libfaac
AudioSampleRate 44100
</Stream>

Could anyone pleaseee help me with these formats.. 

Thanks in advance

---

### Post by CrusaderAD on 2009-03-19
I had problems with ffmpeg when I setup a server. I installed the one in synaptic. Which one are you using? Did you download some other version?

---

### Post by d2009 on 2009-03-19
I followed this link to setup ffmpeg on my Ubuntu hardy.. [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

But since few formats are getting streamed properly, i guess, there is no problem with ffmpeg.. Also, i am able to convert them to any given format using ffmpeg command directly. So i believe there is some problem with ffserver.conf...

could you please let me know where exactly am i goin wrong.?

---

### Post by CrusaderAD on 2009-03-19
You installed the server edition right? You may not want to do this, but I did. I installed the Desktop GUI on the server with this:

```
sudo apt-get install ubuntu-desktop
```

Make sure the cd is in the tray. I found it a bit easier to play with the packages and see what's going on with the server by doing this. Plus you can navigate to the host all on the same machine. See what synaptic has for ffmpeg. I know it's working just fine on our server. If you want to check it out, take a look:

[http://www.emuscle.com]("http://www.emuscle.com")

It's all in PHP using ffmpeg for video streaming. Hopefully that helps.

---

### Post by FakeOutdoorsman on 2009-03-19
I'm not sure if FFserver works with mp4, 3gp, and mov.  According to the [sample FFserver config](http://ffmpeg.mplayerhq.hu/sample.html) file:
> # Format of the stream : you can choose among:
# mpeg       : MPEG-1 multiplexed video and audio
# mpegvideo  : only MPEG-1 video
# mp2        : MPEG-2 audio (use AudioCodec to select layer 2 and 3 codec)
# ogg        : Ogg format (Vorbis audio codec)
# rm         : RealNetworks-compatible stream. Multiplexed audio and video.
# ra         : RealNetworks-compatible stream. Audio only.
# mpjpeg     : Multipart JPEG (works with Netscape without any plugin)
# jpeg       : Generate a single JPEG image.
# asf        : ASF compatible streaming (Windows Media Player format).
# swf        : Macromedia Flash compatible stream
# avi        : AVI format (MPEG-4 video, MPEG audio sound)
I've never used FFserver, so I can't help much.  Did you read the sparse [FFserver Documentation](http://www.ffmpeg.org/ffserver-doc.html)?  Perhaps a good first step in debugging this would be to separate the audio and video of your offending AVI and see if one of those is the culprit:
```
ffmpeg -i input.avi -acodec copy output.mp2
ffmpeg -i input.avi -vcodec copy -an output.avi
```

---

### Post by d2009 on 2009-03-20
@raptormanad - I am afraid that link was of no help. And i have to do this on server only rather than desktop as per the requirements.. I played with the desktop and server equally.. and every format is getting converted to every other format using the normal ffmpeg commands. But I am stuck with ffserver when i am trying to do the same (esp for .mov,.avi, .3gp formats). So could you suggest me something on that part. 
Thanks

@FakeOutdoorsman - The ffmpeg command works fine. But when i do that with ffserver, irrespective of audio, video or audio&video.. everything is waiting endlessly.. and sometimes now giving errors like " muxer does not support non seekable output" , "Error writing output header" .. I am soo badly stuck here.. Could you please suggest me something.

And like you said, i guess it does support those formats. But even i am not sure 100% on that.  
Thanks

---

### Post by CrusaderAD on 2009-03-25
Maybe you need the restricted extras installed?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by flaviocapaccio on 2012-07-03
> **d2009 said:**
> @raptormanad - I am afraid that link was of no help. And i have to do this on server only rather than desktop as per the requirements.. I played with the desktop and server equally.. and every format is getting converted to every other format using the normal ffmpeg commands. But I am stuck with ffserver when i am trying to do the same (esp for .mov,.avi, .3gp formats). So could you suggest me something on that part. 
Thanks

@FakeOutdoorsman - The ffmpeg command works fine. But when i do that with ffserver, irrespective of audio, video or audio&video.. everything is waiting endlessly.. and sometimes now giving errors like " **muxer does not support non seekable output**" , "**Error writing output header**" .. I am soo badly stuck here.. Could you please suggest me something.

And like you said, i guess it does support those formats. But even i am not sure 100% on that.  
Thanks

I'm having the same problems. Did anyone solve this problem?

---

### Post by oldos2er on 2012-07-03
Old thread closed. If you have a question please start a new thread.

---

