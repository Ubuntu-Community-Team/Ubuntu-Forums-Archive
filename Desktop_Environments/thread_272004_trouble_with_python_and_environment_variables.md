---
title: "trouble with python and environment variables"
date: 2006-10-05
forum: Desktop Environments
---

### Post by nwillis on 2006-10-05
Heyo.  I need some help from a knowledgable python person, I think.  I've installed [boodler]("http://www.eblong.com/zarf/boodler"), which is a python-based "soundscaping" app.  Basically, you create formulas and the app generates sounds on the fly, so it sounds like natural waves, crickets, whatever.

Anyway, the problem is this.  Boodler depends on two environment variables, BOODLER_SOUND_PATH and BOODLER_EFFECTS_PATH.  I have set both and exported them like so:
[INDENT]BOODLER_SOUND_PATH=/opt/boodler-snd
BOODLER_EFFECTS_PATH=/opt/boodler/effects
export BOODLER_SOUND_PATH
export BOODLER_EFFECTS_PATH[/INDENT]

but still, when I run a simple boodler effect, it complains that it can't find the sounds (the message is "boodle.sample.SampleError: file not readable: pure/steroeotest.aiff").

Weirder still, if I set both environment variables on the command line as I'm calling boodler, ie:
[INDENT]$ BOODLER_SOUND_PATH=/opt/boodler-snd BOODLER_EFFECTS_PATH=/opt/boodler/effects python boodler.py play.OneSound pure/stereotest.aiff[/INDENT]
...all on one line, it works just fine.

What is the difference?  Why can python understand the environment variable in one instance, but not in the other?  I can check that the variables are set with a plain old "export" -- and they are.  It's just that the app isn't comprehending them if they're set/exported in a separate command.

I'm lost.

The only other piece of info I can think of that might be relevant is from the code itself.  It appears that BOODLER_SOUND_PATH is imported inside the program by this statement:
[INDENT]sound_dirs = os.environ.get('BOODLER_SOUND_PATH', os.curdir)
sound_dirs = string.split(sound_dirs, ':')[/INDENT]
and BOODLER_EFFECTS_PATH by:
[INDENT]effects_dir = os.environ.get('BOODLER_EFFECTS_PATH')
if (effects_dir):
        effects_dir = string.split(effects_dir, ':')
        for dir in effects_dir:
                if (len(dir) > 0):
                        sys.path.append(dir)[/INDENT]

I don't know enough python to tell if either of these is the problem.  Can anyone help?

Nate

---

