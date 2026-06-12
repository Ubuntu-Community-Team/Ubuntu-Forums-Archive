---
title: "xml ECG viewing in Ubuntu"
date: 2010-07-20
forum: Education &amp; Science
---

### Post by ugm6hr on 2010-07-20
Long shot here....

There are a number of XML ECG formats - I am most interested in Philips (which is an open standard).

Does anyone know of a way to view Philips xml ECG files in Ubuntu, perhaps using an Octave filter?  I am aware of people using Matlab to do this kind of thing, but I can't find anything open source.

---

### Post by kanten on 2010-07-29
Hi,

I have some experience dealing with mostly GE XML ECGs and have been researching how to deal with Philips ECGs.
The problem with the Philips ECGs is that the waveform data is compressed somehow. In the XML file is says that the method is "XLI", but I cannot seem to find anything about it on google.

However once you decompress the waveform data is basicly just the y-axis points in a coordinate system. The x-axis is time, incrementing 2ms per new y-axis point. This means you can plot the data in Openoffice Calc if you want to.

If you can find anything about the compression used, then please let me know.

/Anders

---

### Post by incognito on 2010-07-29
Hi:

From googling philips, ecg, and xml:

[http://openmedical.sed.hu/en/szoftverek/konverterek/1](http://openmedical.sed.hu/en/szoftverek/konverterek/1) (decompressor download)

[http://www.openecg.net/whats_new.html](http://www.openecg.net/whats_new.html) (links to software repository where a couple of decompressors / SVG converters (bonus!) are listed)

I did not download software so YMMV. HTH,

incognito

---

### Post by kanten on 2010-07-29
> **incognito said:**
> Hi:

From googling philips, ecg, and xml:

[http://openmedical.sed.hu/en/szoftverek/konverterek/1](http://openmedical.sed.hu/en/szoftverek/konverterek/1) (decompressor download)

[http://www.openecg.net/whats_new.html](http://www.openecg.net/whats_new.html) (links to software repository where a couple of decompressors / SVG converters (bonus!) are listed)
incognito

Have seen both of these. But I would like to decompress the waveform data in my own routines (a PHP-based solution).

/Anders

---

### Post by ugm6hr on 2010-07-31
Indeed, I had found those links in google too, and have subscribed to openecg.

I just wanted to know if anyone had a confirmed solution. The OpenECG software requires XP, which I would prefer not to be reliant upon.

---

### Post by ugm6hr on 2010-08-08
This is actually quite frustrating.

Given Philips proudly state they support an open ECG format, it is essentially untrue given they don't publicise a method to decompress the raw xml data.

Still haven't tried the freeware solution on openecg, but might have to use that route.

---

### Post by panzermensch on 2010-08-18
Hi all.
 
Have any of you decompressed the method is "XLI"?. Please let me know if you have any clue.
 
Thank you!

---

### Post by sixlettervariable on 2011-12-26
I have reverse engineered the XLI compression algorithm and completed (to date) a [reference implementation of the decompression in C#]("http://code.google.com/p/sierra-ecg-tools/").

Basically you need to decode the parsedwaveforms data as follows ([as described in the project]("http://code.google.com/p/sierra-ecg-tools/wiki/XliCompressionScheme")):

[LIST=1]
[*]Base64 decode the XML text
[*]Read the first 8 bytes of the stream
[*]Of those, the first 4 bytes is a 32-bit integer describing the size of the compressed data
[*]The next 2 bytes of the header are unknown at this point
[*]The last 2 bytes of the 8-byte header is the first delta code (used later)
[*]Read the next N-bytes, where N is the length of the compressed chunk data
[*]Decompress the chunk using LZW (10-bit codes)
[*]The decompressed data is 16-bit integers, with the MSB in the first half of the data and the LSB in the second half of the data
[*]Once the decompressed data is reconstituted, it represents a series of 16-bit integer delta codes
[*]After decoding the delta-compression use leads I and II to recreate leads III, aVR, aVL, and aVF
[/LIST]

The delta compression scheme utilizes a sliding window of two delta codes, and can be decompressed as follows:
```
# output contains the 16-bit delta codes
# first is the 16-bit delta code from the chunk header
fun deltaDecompression( output[], nSamples, first )
    x <- output[1]
    y <- output[2]
    prev <- first
    for i <- 3..nSamples
        z <- (2 * y) - x - prev
        prev <- output[i] - 64
        output[i] <- z
        x <- y
        y <- z
    endfor
endfun
```

I hope this helps, even if it is a bit late!

---

