---
title: "GNU Solfege Problem"
date: 2008-05-12
forum: Education &amp; Science
---

### Post by simiris on 2008-05-12
hi...

i can open the programme but there is no sound. The bug report is this:

/usr/share/solfege/soundcard/solfege_c_midi.py:5: RuntimeWarning: Python C API version mismatch for module swig_runtime_data2: This Python has API version 1013, module swig_runtime_data2 has version 1012.

  import _solfege_c_midi


any help plz?
thanks in advance

---

### Post by arekkusu on 2008-05-15
Just installed it on Ubuntu 8.04 and can't even start it.
Here is what I get when I try to run "solfege":

warning: invalid directory in path: /home/alexandre/lessonfiles
Solfege will use fakesynth
/usr/share/solfege/src/mainwin.py:436: GtkWarning: Refusing to add non-unique action '_Rhythm' to action group 'NotExit'
  self.m_action_groups['NotExit'].add_actions(actions)

Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_solfege.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range

:(

---

### Post by arekkusu on 2008-05-15
Don't know if you tried that:

[http://www.solfege.org/Solfege/InstallingSolfege#toc2](http://www.solfege.org/Solfege/InstallingSolfege#toc2)

>If you can start the program, but there is no sound
>
>           sudo apt-get install timidity

---

### Post by Johel Pires on 2008-06-02
I got the same problem as arekkusu reported.. it only shows the splash screen and crashes. the error msg is pretty much the same.

any ideas?

---

### Post by TiddlyPom on 2008-10-29
I have Ubuntu 8.04 (32 bit) installed on a very humble laptop ([Dell Latitude C610]("http://www.pcworld.com/reviews/product/8423/review/latitude_c610.html")) which is plenty fast enough (using the real time kernel) to run [Rosegarden]("http://www.rosegardenmusic.com/") (either connected to a [Yamaha Clavinov]("http://www.yamahamusician.com/clavinova-clp-270-280.html")a (USB) or stand alone using Fluidsynth.

I would recommend installing:

1) [qjackctl]("http://qjackctl.sourceforge.net/")
2) [fluidsynth]("http://fluidsynth.resonance.org/trac")
3) [pmidi]("http://www.parabola.demon.co.uk/alsa/pmidi.html")
4) fluid-soundfont-gm and fluid-soundfont-gs

Disable timidity from starting (if it is installed)
$ sudo update-rc.2 -f timidity

Test everything out first.

Make sure that you can start and stop Jack with qjactctl.  I set mine to minimize to the system tray

[x] Enable system tray icon
[x] Minimize to system tray

For fluidsynth

1) Set the audio driver to jack
2) [Load the soundfont(s)]("http://www.linuxjournal.com/article/8354")
3) In [Options] enable the systen tray icon

I use [pmidi]("http://www.parabola.demon.co.uk/alsa/pmidi.html") (connected to [fluidsynth]("http://fluidsynth.resonance.org/trac")) to play sounds within [Solfege]("http://www.solfege.org/").

Try it all out at this stage.  
Run **pmidi -l** and find fluidsynth (e.g. 129:0)
Play a midi file (e.g.)

$ pmidi -p 129:0 test.mid

and the music should play :)

1) Within GNU Solfege select File -> Preferences -> Sound setup (tab)
2) Alter .midi file player to be **/usr/bin/pmidi -P 129:0 %s**
3) Change the radio buttons at the bottom to be **Use external midiplayer**

If you cannot get solfege to run at all (starts and immediately stops) then run solfege from a terminal like this:

$ solfege --no-sound

and you should be able to get around the crash.

Hope this helps :)

---

### Post by TiddlyPom on 2008-10-29
Oops! A couple of slight corrections :)

1) To disable timidity use **sudo update-rc.d -f timidity remove**
2) For playing midi files the line should be **/usr/bin/pmidi -p 129:0 %s**

---

