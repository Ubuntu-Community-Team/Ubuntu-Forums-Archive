---
title: "Redirect the master playback OUT to capture IN..."
date: 2009-02-19
forum: General Help
---

### Post by saswatnits on 2009-02-19
I hope I am posting this in the right forum... 

I want to 'play' some sound file over skype or ekiga. I think the way to do this will be to play the file in any media player, and redirect the playback to the capture options, so that when i call someone in skype instead of taking the input from my microphone the input is captured from the file being played.

 How can I do this in Ubuntu using alsa? Is there a better way to do this instead of redirecting the playback out to capture in?

I hope my question is clear. Does anybody know how to do this? 
Thanks for your help.
 - Saswat.

---

### Post by saswatnits on 2009-05-09
I think nobody understood what I am telling. Well..

I am trying to test a VoIP application. I have two machines A & B. I want to listen and rate the quality of the Voice transfer at Machine B. The VoIP app on Machine A needs to send the voice traffic. Now I cannot talk on Machine A and listen on Machine B at the same time.. Hence I want to play some audio file on A and redirect that playback to the capture device (mic or whatever), so that it is sent over to B.

Now I am using a Nvidia audio driver..

lshw output
 *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation

Please let me know what I can do. THanks for the help.

---

### Post by Acapulco on 2009-05-09
Without knowing much about the audio system, I think the approach you proposed will work ok (albeit very non-geekish). Just plug some cd player or something to the mic line.

It's not elegant but it should work.

Otherwise I think it would depend a lot on the driver you are using, and I wouldn't be too sure about how easy it is to configure for your purposes. Rerouting audio should be doable but not trivial I believe.

Sorry to be of little help :/

---

### Post by saswatnits on 2009-05-09
I can try that for sure.. But I was looking for something like 'Record what you hear" functionality available on Realtek cards on WinXP. Can anyone suggest if I should post this question in some other specific forum.

Thanks.

---

### Post by smkururu on 2009-05-11
I'm searching for a solution simmiliar to this one too, but I can't still get it. For the meantime, you could try using a short enough audio cable (both males, fit your soundcard) and link the output to input.

---

