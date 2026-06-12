---
title: "Gstreamer Help"
date: 2009-06-01
forum: General Help
---

### Post by illbashu on 2009-06-01
```
bash@bash-desktop:~/Desktop/Download/gst-python-0.10.152$ sudo make install
Making install in common
Making install in m4
Making install in codegen
Making install in gst
Making install in extend
 /usr/bin/install -c -m 644 '__init__.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/__init__.py'
 /usr/bin/install -c -m 644 'pygobject.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/pygobject.py'
 /usr/bin/install -c -m 644 'utils.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/utils.py'
 /usr/bin/install -c -m 644 'discoverer.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/discoverer.py'
 /usr/bin/install -c -m 644 'sources.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/sources.py'
 /usr/bin/install -c -m 644 'leveller.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/leveller.py'
 /usr/bin/install -c -m 644 'jukebox.py' '/usr/lib/python2.6/dist-packages/gst-0.10/gst/extend/jukebox.py'
Byte-compiling python modules...
__init__.py pygobject.py utils.py discoverer.py sources.py leveller.py jukebox.py
Byte-compiling python modules (optimized versions) ...
__init__.py pygobject.py utils.py discoverer.py sources.py leveller.py jukebox.py
  CC    gst-argtypes.o
  CC    gstmodule.o
  CC    pygstiterator.o
  CC    pygstminiobject.o
  CC    pygstvalue.o
  CC    pygstexception.o
Traceback (most recent call last):
  File "../codegen/codegen.py", line 1574, in <module>
    sys.exit(main(sys.argv))
  File "../codegen/codegen.py", line 1531, in main
    o = override.Overrides(arg, path=extendpath)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 49, in __init__
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 174, in __parse_override
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 174, in __parse_override
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 104, in __parse_override
    command = words[0]
IndexError: list index out of range
make[3]: *** [gst.c] Error 1
make[2]: *** [install-recursive] Error 1
make[1]: *** [install-recursive] Error 1
make: *** [install] Error 2

```

```
bash@bash-desktop:~/Desktop/Download/gst-python-0.10.152$ sudo make check
Making check in common
Making check in m4
Making check in codegen
Making check in gst
Making check in extend
Traceback (most recent call last):
  File "../codegen/codegen.py", line 1574, in <module>
    sys.exit(main(sys.argv))
  File "../codegen/codegen.py", line 1531, in main
    o = override.Overrides(arg, path=extendpath)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 49, in __init__
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 174, in __parse_override
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 174, in __parse_override
    self.handle_file(filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 92, in handle_file
    self.__parse_override(buf, startline, filename)
  File "/home/bash/Desktop/Download/gst-python-0.10.152/codegen/override.py", line 104, in __parse_override
    command = words[0]
IndexError: list index out of range
make[3]: *** [gst.c] Error 1
make[2]: *** [check-recursive] Error 1
make[1]: *** [check-recursive] Error 1
make: *** [check] Error 2

```

I am trying to install gst-python-0.10.15 for use with pitivi but i keep getting that error message.

---

### Post by ptsubin on 2009-06-01
Why don't you use synaptic for this?

---

### Post by Yellow Pasque on 2009-06-01
> **ptsubin said:**
> Why don't you use synaptic for this?
the pitivi project requires gst-python >= 0.10.15

If you want to compile from source, you'll need to build gstreamer0.10-23 itself first.
Or you could grab pre-built gstreamer .debs from a PPA like: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by illbashu on 2009-06-02
> **Temüjin said:**
> the pitivi project requires gst-python >= 0.10.15

If you want to compile from source, you'll need to build gstreamer0.10-23 itself first.
Or you could grab pre-built gstreamer .debs from a PPA like: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

I added that to my source list and it updated them but now I am getting this :/

```

Could not find the GNonLin plugins!
 
Make sure the plugins were installed and are available in the GStreamer plugins path.

```
edit... i figured it out...

---

### Post by illbashu on 2009-06-02
I tried running it and it wouldn't give a an output (like missing package or something) or start so i ran it in terminal and i got this...

```

bash@bash-desktop:~$ pitivi
Traceback (most recent call last):
  File "/usr/local/bin/pitivi", line 118, in <module>
    _run_pitivi()
  File "/usr/local/bin/pitivi", line 113, in _run_pitivi
    sys.exit(ptv.main(sys.argv))
  File "/usr/local/lib/pitivi/python/pitivi/application.py", line 362, in main
    add_to_timeline=options.add_to_timeline)
  File "/usr/local/lib/pitivi/python/pitivi/application.py", line 275, in __init__
    Pitivi.__init__(self, *args, **kwargs)
  File "/usr/local/lib/pitivi/python/pitivi/application.py", line 130, in __init__
    self.newBlankProject()
  File "/usr/local/lib/pitivi/python/pitivi/application.py", line 233, in newBlankProject
    track = Track(video)
  File "/usr/local/lib/pitivi/python/pitivi/timeline/track.py", line 318, in __init__
    self.setDefaultTrackObject(default_track_object)
  File "/usr/local/lib/pitivi/python/pitivi/timeline/track.py", line 352, in setDefaultTrackObject
    self.addTrackObject(track_object)
  File "/usr/local/lib/pitivi/python/pitivi/timeline/track.py", line 400, in addTrackObject
    track_object.makeBin()
  File "/usr/local/lib/pitivi/python/pitivi/timeline/track.py", line 239, in makeBin
    bin = self.factory.makeBin(self.stream)
  File "/usr/local/lib/pitivi/python/pitivi/factories/base.py", line 244, in makeBin
    bin = self._makeBin(compatible_stream)
  File "/usr/local/lib/pitivi/python/pitivi/factories/test.py", line 41, in _makeBin
    videotestsrc = gst.element_factory_make('videotestsrc')
gst.ElementNotFoundError: videotestsrc

```

---

