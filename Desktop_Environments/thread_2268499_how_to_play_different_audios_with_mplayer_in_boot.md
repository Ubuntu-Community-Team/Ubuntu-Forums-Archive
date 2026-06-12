---
title: "how to play different audios with mplayer in boot"
date: 2015-03-09
forum: Desktop Environments
---

### Post by Filisteus on 2015-03-09
Hello Guys!
 I format computers in my town, only if the customer accepts linux, and set up a friendly environment with all the facilities according to the customer profile.
 But a client ask me that every login I add a different audio.
 I use a script with mplayer to play an audio. but if I use the "mplayer --shufle * .ogg" it touches all audios directory and I want to play just one and exit.
How i do it?

---

### Post by dino99 on 2015-03-09
i've never done it, but it looks like you simply need a playlist loaded, with the selected songs list

---

### Post by mainmeister on 2015-03-09
What I would do is write a script. The script will need to build a list of all of the audio file names. After building the file name list, select one of the names using a random number generator. An alternative would be to prebuild the list of file names and hard code the list into a file and just read the file in the script and select a random line out of the file. You could do this in a shell script, python, javascript, or pretty much any other scripting language. There is no reason you could not create a small c program to do this as well.

Once the random audio file name is selected it is a simple matter to run mplayer with the selected file name.

---

### Post by mainmeister on 2015-03-09
[http://pastebin.com/Y12bNX2e](http://pastebin.com/Y12bNX2e)

"""
    Play a random file with mplayer

    python PlayRandomSong.py path
"""
import argparse
import os
import random
from subprocess import call

def playRandom(path):
    print path
    filenames = os.listdir(path)
    call("mplayer '" + os.path.join(path, filenames[int(random.random() * (len(filenames) - 1))]) + "'", shell = True)

if __name__ == '__main__':
    parser = argparse.ArgumentParser('python PlayRandomSong')
    parser.add_argument('path')
    args = parser.parse_args()
    playRandom(args.path)

---

### Post by Filisteus on 2015-03-10
Excuse my ignorance!
 But how do I use this script?

> **mainmeister said:**
> [http://pastebin.com/Y12bNX2e](http://pastebin.com/Y12bNX2e)

"""
    Play a random file with mplayer

    python PlayRandomSong.py path
"""
import argparse
import os
import random
from subprocess import call

def playRandom(path):
    print path
    filenames = os.listdir(path)
    call("mplayer '" + os.path.join(path, filenames[int(random.random() * (len(filenames) - 1))]) + "'", shell = True)

if __name__ == '__main__':
    parser = argparse.ArgumentParser('python PlayRandomSong')
    parser.add_argument('path')
    args = parser.parse_args()
    playRandom(args.path)

---

