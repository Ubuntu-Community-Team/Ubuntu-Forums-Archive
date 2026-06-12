---
title: "gstreamer pipeline options for Sound Juicer"
date: 2005-12-30
forum: Desktop Environments
---

### Post by tjfitz on 2005-12-30
I have found a lot of info on the forums about how to get Sound Juicer set up for ripping to mp3 format. Most of the posts include placing something like "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=*blah*" in the "GStreamer Pipeline" field. I have gathered enough info to do some basic things, but what I'd really like to know is, what are all the variables that are available to use in this field? It's easy to just cut-n-paste, but I like doing things the hard way. 

If you just know how to normalize my output file that will be helpful too. Or if you know how to normalize them and use high-quality vbr with a max bitrate of 192.... (yeah, I know, "...max-bitrate=192")

---

### Post by Curufir on 2005-12-31
Use gst-inspect, could be gst-inspect-0.8.

If you use it without a plugin name you'll get a list of all your plugins.

If you use it with a plugin name then you'll get a list of the plugin's information.

E.g.

Ogg Vorbis encoding.

```

gst-inspect rawvorbisenc

Factory Details:
  Long name:    Vorbis encoder
  Class:        Codec/Encoder/Audio
  Description:  Encodes audio in Vorbis format
  Author(s):    Monty <monty@xiph.org>, Wim Taymans <wim@fluendo.com>
  Rank:         none (0)

Plugin Details:
  Name:         vorbis
  Description:  Vorbis plugin library
  Filename:     /usr/lib/gstreamer-0.8/libgstvorbis.so
  Version:      0.8.11
  License:      LGPL
  Package:      GStreamer Plugins (Debian)
  Origin URL:   http://packages.qa.debian.org/gst-plugins0.8

GObject
 +----GstObject
       +----GstElement
             +----VorbisEnc

Implemented Interfaces:
  GstTagSetter

Pad Templates:
  SINK template: 'sink'
    Availability: Always
    Capabilities:
      audio/x-raw-float
                   rate: [ 8000, 50000 ]
               channels: [ 1, 2 ]
             endianness: 1234
                  width: 32
          buffer-frames: 0

  SRC template: 'src'
    Availability: Always
    Capabilities:
      audio/x-vorbis


Element Flags:
  GST_ELEMENT_EVENT_AWARE

Element Implementation:
  No loopfunc(), must be chain-based or not configured yet
  Has change_state() function: 0xb7fe8f60
  Has custom save_thyself() function: gst_element_save_thyself
  Has custom restore_thyself() function: gst_element_restore_thyself

Element has no clocking capabilities.
Element has no indexing capabilities.

Pads:
  SINK: 'sink'
    Implementation:
      Has chainfunc(): 0xb7fe810d
      Supports seeking/conversion/query formats:
                (2):    bytes (Bytes)
                (1):    default (Default format for the media type)
                (3):    time (Time)
      Has custom convertfunc(): gst_vorbisenc_convert_sink
    Pad Template: 'sink'
  SRC: 'src'
    Implementation:
      Supports seeking/conversion/query formats:
                (2):    bytes (Bytes)
                (3):    time (Time)
      Has custom convertfunc(): gst_vorbisenc_convert_src
      Has custom queryfunc(): gst_vorbisenc_src_query
        Provides query types:
                (1):    total (Total length)
                (2):    position (Current Position)
    Pad Template: 'src'

Element Properties:
  name                : The name of the object
                        String. Default: "(null)" Current: "vorbisenc0"
  max-bitrate         : Specify a maximum bitrate (in bps). Useful for streaming applications. (-1 == disabled)
                        Integer. Range: -1 - 250001 Default: -1 Current: -1
  bitrate             : Attempt to encode at a bitrate averaging this (in bps). This uses the bitrate management engine, and is not recommended for most users. Quality is a better alternative. (-1 == disabled)
                        Integer. Range: -1 - 250001 Default: -1 Current: -1
  min-bitrate         : Specify a minimum bitrate (in bps). Useful for encoding for a fixed-size channel. (-1 == disabled)
                        Integer. Range: -1 - 250001 Default: -1 Current: -1
  quality             : Specify quality instead of specifying a particular bitrate.
                        Float. Range:               0 -               1 Default:             0.3 Current:             0.3

  managed             : Enable bitrate management engine
                        Boolean. Default: false Current: false
  last-message        : The last status message
                        String. Default: "(null)" Current: ""

```

All pretty boring until you reach the Element Properties part which gives you information about all the flags you can use in your gstreamer profile. Lame will have something similar.

---

### Post by tjfitz on 2005-12-31
That is exactly what I was looking for.  Thanks a bunch! :D

---

### Post by tjfitz on 2005-12-31
Silly me, now I remember that the ripped tracks have to be normalized BEFORE they are encoded to mp3. I just mucked around with gst-inspect (wavpack, wavpackparse, wavpackdec, waveparse) but didn't find anything helpful; the only "element properties" these had were "name".

Anybody know how to normalize the raw track?  I think Grip's "Calculate Gain Adjustment" is roughly the same thing.

(In a nutshell, I want to volume level of each ripped track to be increased to nearly the maximum allowable amount).

 Also, if you know the general syntax used in the "gstreamer pipeline" field, that would be nice to know!

---

