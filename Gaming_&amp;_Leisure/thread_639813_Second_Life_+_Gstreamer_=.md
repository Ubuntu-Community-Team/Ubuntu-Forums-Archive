---
title: "Second Life + Gstreamer = ???"
date: 2007-12-13
forum: Gaming &amp; Leisure
---

### Post by werewolfzx8 on 2007-12-13
I can't seem to find an answer anywhere. So far everybody claims that Second Life and Gstreamer work flawlessly, but I can't seem to get it to work O.o;;

Music streams just fine, but when I click to stream live video... nothing happens. It sits there for a few seconds, sometimes frozen, and then the stop button grays out again.


I tried running it from the terminal, it's kinda hard to see what's going on cause the following just keeps poping up:
```

2007-12-13T21:03:30Z WARNING: ll_apr_warn_status: APR: Connection refused
2007-12-13T21:03:31Z WARNING: ll_apr_warn_status: APR: Connection refused
2007-12-13T21:03:32Z WARNING: ll_apr_warn_status: APR: Connection refused
2007-12-13T21:03:33Z WARNING: ll_apr_warn_status: APR: Connection refused

```

And the following was after I pushed the play button:
```

2007-12-13T21:06:43Z INFO: looping media... 0
2007-12-13T21:06:43Z INFO: playing media...
2007-12-13T21:06:47Z INFO: idle: Kills on unknown objects: 6
** Message: don't know how to handle text/html
2007-12-13T21:06:47Z INFO: sendToSim: Sending throttle settings, total BW 700
2007-12-13T21:06:47Z INFO: updateDynamicThrottle: Tightening network throttle to 716800
2007-12-13T21:06:47Z WARNING: ll_apr_warn_status: APR: Connection refused
2007-12-13T21:06:47Z INFO: my_bus_callback: Got GST message type: clock-provide
2007-12-13T21:06:47Z INFO: my_bus_callback: Got GST message type: element
2007-12-13T21:06:47Z INFO: my_bus_callback: Got GST message type: error
2007-12-13T21:06:47Z INFO: my_bus_callback: GST error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
2007-12-13T21:06:47Z INFO: stopping media...
2007-12-13T21:06:47Z INFO: my_bus_callback: Got GST message type: error
2007-12-13T21:06:47Z INFO: my_bus_callback: GST error: Internal data flow error.
2007-12-13T21:06:47Z INFO: stopping media...

```

---

### Post by werewolfzx8 on 2007-12-20
Sorry for the double post but I really need to figure this out now...

I'm about to go to work, so there's not much I can try right away, but here's the exact output of when I try to play a movie:

```
2007-12-20T15:01:56Z INFO: looping media... 0
2007-12-20T15:01:56Z INFO: playing media...
2007-12-20T15:01:57Z WARNING: ll_apr_warn_status: APR: Connection refused
2007-12-20T15:01:58Z INFO: my_bus_callback: Got GST message type: clock-provide
2007-12-20T15:01:58Z INFO: my_bus_callback: Got GST message type: error
2007-12-20T15:01:58Z INFO: my_bus_callback: GST error: Resource not found.
2007-12-20T15:01:58Z INFO: stopping media...

```

However playing music works just fine.

---

### Post by werewolfzx8 on 2007-12-20
Sorry to bump this again...

I'm going to look further into it myself once I get home, and also post in the SL community.

I've googled and can find problems that are close, but not the one I'm having...

---

### Post by werewolfzx8 on 2007-12-21
I managed to get the APR error fixed (I had Voice Chat enabled).

Onto the real problem...

I've been searching around, but still have not found a solution quite yet...

here is what I'm getting now, every time I try to play a video:
```
2007-12-21T12:07:36Z INFO: grab_gst_syms: Found DSO: libgstreamer-0.10.so.0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_init_check from 0xab5386e0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_get_type from 0xab55e4c0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_type_get_name from 0xab55e410
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_parse_error from 0xab55e790
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_parse_warning from 0xab55e670
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_parse_state_changed from 0xab55eb80
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_set_state from 0xab54d580
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_object_unref from 0xab539680
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_object_get_type from 0xab539930
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_pipeline_get_type from 0xab56c680
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_pipeline_get_bus from 0xab56c610
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_bus_add_watch from 0xab544590
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_factory_make from 0xab553b90
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_get_type from 0xab54d1e0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_static_pad_template_get from 0xab56bcf0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_class_add_pad_template from 0xab54f730
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_class_set_details from 0xab54f680
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_unref from 0xab546a30
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_ref from 0xab5462d0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: _gst_debug_register_funcptr from 0xab55ad10
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: _gst_debug_category_new from 0xab55c360
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_is_empty from 0xab546470
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_from_string from 0xab547c90
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_replace from 0xab546be0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_get_structure from 0xab546560
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_copy from 0xab547de0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_caps_intersect from 0xab548420
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_element_register from 0xab553670
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: _gst_plugin_register_static from 0xab56ff40
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_structure_get_int from 0xab578b40
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_structure_get_value from 0xab577b60
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_value_get_fraction_numerator from 0xab58e6a0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_value_get_fraction_denominator from 0xab58e630
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_structure_get_name from 0xab5787f0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_segtrap_set_enabled from 0xab536e30
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_parse_buffering from 0xab55ec90
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_message_parse_info from 0xab55e550
2007-12-21T12:07:36Z INFO: grab_gst_syms: Found DSO: libgstaudio-0.10.so.0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_audio_sink_get_type from 0xad1aa050
2007-12-21T12:07:36Z INFO: grab_gst_syms: Found DSO: libgstvideo-0.10.so.0
2007-12-21T12:07:36Z INFO: grab_gst_syms: grabbed symbol: gst_video_sink_get_type from 0xad07a2f0
2007-12-21T12:07:36Z INFO: load: Setting media URI: [http://www.movie-list.net/classics/army-of-darkness.mov](http://www.movie-list.net/classics/army-of-darkness.mov)
2007-12-21T12:07:36Z INFO: load returns 1
2007-12-21T12:07:36Z INFO: looping media... 0
2007-12-21T12:07:36Z INFO: playing media...
FSOUND_Output_OSS_Wait : Timeout on audio write. Caused by bad driver!
FSOUND_Output_OSS_Wait : Timeout on audio write. Caused by bad driver!
2007-12-21T12:07:37Z INFO: my_bus_callback: Got GST message type: clock-provide
** Message: don't know how to handle text/html
2007-12-21T12:07:37Z INFO: my_bus_callback: Got GST message type: element
2007-12-21T12:07:37Z INFO: my_bus_callback: Got GST message type: error
2007-12-21T12:07:37Z INFO: my_bus_callback: GST error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
2007-12-21T12:07:37Z INFO: stopping media...
2007-12-21T12:07:37Z INFO: my_bus_callback: Got GST message type: error
2007-12-21T12:07:37Z INFO: my_bus_callback: GST error: Internal data flow error.
2007-12-21T12:07:37Z INFO: stopping media...
```

I have every GStreamer package I can find installed, but it's all through synaptic. I would also like to mention that .mov files work in Totem, but when I try to stream it from the URL, I get the following:

```

The playback of this movie requires a text/html decoder plugin which is not installed.
```
Help please >.<

---

### Post by werewolfzx8 on 2007-12-21
Ok, so somebody mentioned, it might be because of where the Movie(s) is streaming from.

It seems to be a bad link, and I have to agree...

Anybody who has streaming video work, can you tell me where there is streaming video that works for you?

I've also tried the Rox Media Center, but nothing happens.

---

### Post by werewolfzx8 on 2007-12-22
I'm so close!!!!

So I found a video stream that works.
I kept getting a jackd error, so I installed it from the repos.

Now, I'm getting this:
```
2007-12-22T14:31:09Z INFO: playing media...
2007-12-22T14:31:09Z INFO: my_bus_callback: Got GST message type: clock-provide
theQuickTimeDispatcher caught -> 0x6693c3e0
2007-12-22T14:31:09Z INFO: my_bus_callback: Got GST message type: tag
2007-12-22T14:31:09Z INFO: my_bus_callback: Got GST message type: tag
2007-12-22T14:31:09Z INFO: my_bus_callback: Got GST message type: clock-provide
JACK tmpdir identified as [/dev/shm]
2007-12-22T14:31:10Z INFO: my_bus_callback: Got GST message type: error
2007-12-22T14:31:10Z INFO: my_bus_callback: GST error: Resource not found.
2007-12-22T14:31:10Z INFO: stopping media...
WARNING! Invalid Ptr handle!
2007-12-22T14:31:10Z INFO: my_bus_callback: Got GST message type: clock-provide
2007-12-22T14:31:10Z INFO: my_bus_callback: GST buffering: 0%
2007-12-22T14:31:10Z INFO: my_bus_callback: GST buffering: 2%
2007-12-22T14:31:10Z INFO: my_bus_callback: GST buffering: 5%
2007-12-22T14:31:10Z INFO: my_bus_callback: GST buffering: 8%
2007-12-22T14:31:10Z INFO: my_bus_callback: GST buffering: 11%

```

Each time I try to play it again, it buffers less, and then it freezes...

I know I've seen this in the SL forums some where, so I'll keep looking...

Edit:
I  found the thread on the SL forums, but not even Tofu knew what was going on. I don't see a solution to the problem either. This is with ALL movies that I try to play...

See [This Thread]("http://forums.secondlife.com/showthread.php?t=201623") for more information.

---

### Post by scwalla on 2007-12-28
I seem to be having the same problem.  I have not found any answer to this.  I can watch videos in Totem/Gstreamer but not in SL client. I get: "GST error: Resource not found"

---

### Post by bdoe on 2008-08-23
Sorry for necroing such an old thread, but....

Well, you're doing far better than I am. Any time I click on a TV anywhere in SL, or press Play on the streaming media notification, my client instantly crashes - every time. If I have "Automatically play streaming media" set in preferences, I am 100% guaranteed to crash any time I enter a region with streaming media. Nothing useful shows up in any of my SL logs to even point me to the probable cause of the problem.

Any clues?

---

### Post by Darkheart on 2009-02-13
I have been battling this for some time, I have used the open source code, built my own, used SL's ...... right now out of total frustration I have deleted all my own work (I am NOT a talented coder.. just tried to get the danged video to work- dozens of non-functioning versions cluttering my drive.) and just thought that maybe it was a power beyond me. So I waited for Infuriating Ibex to cure the problem?  No such luck.  

SOooo..on that note and poking at a long dormant thread.  

Did you get video on SL to work?  and HOW?

I get very similar errors.  "You might need to install a plugin"


uhh.. I have every plugin installed I can find.  The Good, bad and the ugly! (Thanks for that Mr. Eastwood!)

 And still...  It doesnt' lock up, just have the error in the window I launch from (always launch in the window- I like ot watch the codes scroll by to keep a tab on things.) and I get no results otherwise. 

What was your cure- if you ever got one?

---

### Post by Naiki Muliaina on 2009-02-13
I had the snotting thing working once. Never wrote down what i did, never had it work scince >.<

---

