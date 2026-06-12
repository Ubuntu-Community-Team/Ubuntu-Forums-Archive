---
title: "gnormalize &amp; normalize (without decode, re-encode)"
date: 2006-01-13
forum: General Help
---

### Post by robenroute on 2006-01-13
According to normalize's documentation (see [http://normalize.nongnu.org/](http://normalize.nongnu.org/) ), having the MAD library installed should allow normalize to operate on MP3s, without decoding to WAVs en then re-encoding the sound files).

1. Can anyone confirm this (I've already dropped the developer a line, but no reply yet)?

2. Can gnormalize make use of this feature (on gnormalize's website, there's no mentioning of this)?

Thanks a lot in advance.

Rob

---

### Post by robenroute on 2006-01-15
I thought I'd drop the author of gnormalize (Claudio Fernandez) a line and here's his reply (and my initial question):

> 
Hi, Rob.

'normalize' to normalize directly it uses replaygain
(or some like idea). See the website
([http://www.replaygain.org/)](http://www.replaygain.org/)).

'normalize' calculates the normalization level and put
this informations inside the Metadata (tag) of MP3,
without
the need to decode and re-encode. This way, the MP3
files is not changed (only its tag). But, to use this
functionality, all the MP3 players need to read that
informations inside the tag to control the sound
levels of MP3 files. XMMS (and some others) has a
plugin of normalize that works. But, not all players
uses this plugin!!

gnormalize is an alternative for replaygain, because
"there is no consistent standard by which to define
the appropriate replay gain which mp3 encoders and
players agree on, and no automatic way to set the
volume adjustment for each track".

This is now clear?

Bye. Thanks, Claudio.


--- Rob <> wrote:

> Hi there,
>  
> gnormalize looks like a very interesting program.
> On the website ([http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/))
> it says that gnormalize uses normalize to do the
> actual work. It also says on the same website that
> the way normalization works is that MP3s are first
> decoded to WAV files, these WAV files are then
> normalized and finally the WAVs are encoded back to
> MP3 format.
>  
> According to the normalize website  at
> [http://www1.cs.columbia.edu/~cvaill/normalize/](http://www1.cs.columbia.edu/~cvaill/normalize/) , it
> says that MP3s can be normalized directly, without
> the need to decode and re-encode, and thus avoiding
> quality loss.
>  
>  Is this functionality supported by gnormalize? It
> would be crucial to me and, I'm sure, many others.
>  
>  Thanks.
>  
>  Rob
>  

So, according to Claudio, this means that gnormalize can add volume normalization tags to MP3 files, directly (without decoding and re-encoding). Furthermore, it does the actual calculations using the ReplayGain algorithm.

This is great news! Since Quod Libet (and some others; wich ones?) is capable of reading replaygain (album and track) tags and doing volume adjustments based on these tags, I'm going to be a happy camper (and with me, I assume, a lot of other people).

Regards.

---

### Post by phetre on 2006-05-22
[QUOTE=robenroute]ISo, according to Claudio, this means that gnormalize can add volume normalization tags to MP3 files, directly (without decoding and re-encoding). Furthermore, it does the actual calculations using the ReplayGain algorithm.[/QUOTE]

That would be great news indeed, but I don't think it's the case.  I just installed gnormalize 0.49 from the rpm, and it seems to insist on actually normalizing the waveform.  This is confirmed by the program's description on the Sourceforge page:

> gnormalize decodes the MP3/MP4/MPC/OGG/APE/FLAC file to WAV, then normalizes the WAV to a targeted volume level and re-encodes it.

Later on, that paragraph does mention editing metadata, but this is in the context of extra features (gnormalize also functions as a ripper, transcoder, and player as well as tag editor).  In light of all this, I believe Claudio's claim that "gnormalize is an alternative for replaygain" should read: "gnormalize is an alternative ***to*** replaygain."

To me, this is disappointing, because (if I'm not mistaken) the de- and re-encoding process entails a loss of quality.  Does anyone know a Gnome frontend to replaygain and vorbisgain, which adjust only the metadata?

---

