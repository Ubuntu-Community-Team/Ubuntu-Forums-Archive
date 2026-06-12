---
title: "Songbird Seg Fault"
date: 2009-05-09
forum: General Help
---

### Post by lvleph on 2009-05-09
I am getting a seg fault for more than just songbird, but I will deal with the other mozilla products later. 

I got songbird 1.1.2 from getdeb and when loading songbird I get a seg fault. I was getting a seg fault on the previous version too. The following is the output in terminal.

```
songbird 

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmxf.so': /usr/lib64/gstreamer-0.10/libgstmxf.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstladspa.so': /usr/lib64/gstreamer-0.10/libgstladspa.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmetadata.so': /usr/lib64/gstreamer-0.10/libgstmetadata.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstqtmux.so': /usr/lib64/gstreamer-0.10/libgstqtmux.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstffmpeg.so': /usr/lib64/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstflv.so': /usr/lib64/gstreamer-0.10/libgstflv.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstgio.so': /usr/lib64/gstreamer-0.10/libgstgio.so: undefined symbol: gst_query_set_uri

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstgnomevfs.so': /usr/lib64/gstreamer-0.10/libgstgnomevfs.so: undefined symbol: gst_query_set_uri

(songbird-bin:30078): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstcelt.so': /usr/lib64/gstreamer-0.10/libgstcelt.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmxf.so': /usr/lib64/gstreamer-0.10/libgstmxf.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstladspa.so': /usr/lib64/gstreamer-0.10/libgstladspa.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmetadata.so': /usr/lib64/gstreamer-0.10/libgstmetadata.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstqtmux.so': /usr/lib64/gstreamer-0.10/libgstqtmux.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstffmpeg.so': /usr/lib64/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_tag_setter_reset_tags

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstflv.so': /usr/lib64/gstreamer-0.10/libgstflv.so: undefined symbol: gst_byte_reader_skip

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstgio.so': /usr/lib64/gstreamer-0.10/libgstgio.so: undefined symbol: gst_query_set_uri

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstgnomevfs.so': /usr/lib64/gstreamer-0.10/libgstgnomevfs.so: undefined symbol: gst_query_set_uri

(songbird-bin:30092): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstcelt.so': /usr/lib64/gstreamer-0.10/libgstcelt.so: undefined symbol: gst_tag_setter_reset_tags
Segmentation fault

```

---

### Post by James78 on 2009-05-09
The GStreamer warnings are happening because you have the latest GStreamer version, and the current stable version of Songbird, 1.1.2, is incompatible with it. The new version in nightly testing works perfectly with the new GStreamer plugins. As for the segmentation fault, can you check if libvisuals-plugins is installed? It may be causing a problem..

In Getsatisfaction, there's another report of a user using a 64-Bit OS like yourself, and nothing we could suggest could get his segmentation fault to go away, maybe it's related.

---

### Post by lvleph on 2009-05-09
No, libvisuals-plugins is not installed. I assume the nightly will have to be compiled and installed?

I am having Seg-Faults in both FF-3.5 and FF-3.6, if that helps with the dignosis.

---

### Post by James78 on 2009-05-09
Nope, the nightly does not have to be compiled. You can download a fully compiled tar.gz from [here]("http://developer.songbirdnest.com/builds/trunk/latest/"). Although, I pretty much suspect that running nightly isn't going to stop your segmentation fault. It would appear to have something to do with 64-Bit. Let me take a look around..

---

### Post by lvleph on 2009-05-10
For some reason I cannot extract those tars. I tried CLI and GUI, nothing.

---

### Post by lvleph on 2009-07-03
The cause of all my segfaults is global-panel-menu.

---

### Post by DJ_Peng on 2009-07-20
Did you have to uninstall the GlobalMenu to get Songbird running or was disabling it good enough? If I have to choose between GlobalMenu and checking out Songbird there's no way I'm uninstalling GM.

---

### Post by lvleph on 2009-07-20
Disbaling it will do the trick. For some reason GlobalMenu only has this as medium priority. I guess when FF 3.5 comes out and everyone stops using Global Menu they may change their minds.

---

### Post by DJ_Peng on 2009-07-20
I actually tried disabling GM and I still got the seg fail. I'd almost think the deb from GetDeb may be borked, but I doubt that. As far as Fx 3.5 coming out, I'm pretty sure it's out already. 

I seriously doubt that you'll see "everyone stop[ing] using Global Menu". Too many users love it, as evidenced by the traffic on the topic on these forums, as well as the requests the Mac4Lin team has gotten to make sure GM gets included in the Mac4Lin 1.0 docs.

---

### Post by lvleph on 2009-07-20
Yeah, but when FF 3.5 is the default browser in 9.10 it is going to be a big issue.

---

### Post by DJ_Peng on 2009-07-20
Just one more reason GNOME's Epiphany is my primary browser. And now I've been able to bump Chromium into my #2 slot, even without plugins.

Of course when I absolutely have to run Firefox I tend to reach for the Fx2 install I make a point of keeping around. Just to make me *really* need to use Fx3 before I fire that bloated bit of software up. 8-)

---

