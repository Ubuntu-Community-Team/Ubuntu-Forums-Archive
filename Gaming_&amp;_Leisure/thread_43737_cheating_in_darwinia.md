---
title: "cheating in darwinia?"
date: 2005-06-23
forum: Gaming &amp; Leisure
---

### Post by farnsworth on 2005-06-23
after trying for ~4 hours to crack the 'game.txt' encryption, I checked google and found someone had already done it. ](*,)   but it wasn't in python.  maybe I'll make it less shamelessly inefficient, and add a pygtk frontend if I get bored tomorrow.

```

"""
encrypts/ decrypts redshirt2 files
"""

class Redshirt:

    __table__ = [31, 7, 9, 1, 11, 2, 5, 5, 3, 17, 40, 12, 35, 22, 27, 2]

    def __init__(self, filename):
        file = open(filename, 'rb')
        self.text = file.read()
        file.close()
        self.charlist = []
        for x in self.text: self.charlist.append(x)

    def save(self, filename):
        file = open(filename, 'w')
        file.write(self.text)
        file.close()

    def decode(self):
        list = []
        i = 0
        self.charlist = self.charlist[9:]
        for char in self.charlist:
            if ord(char) > 32:
                i += 1
                i %= 16
                list.append(chr(ord(char) - self.__table__[i]))
                if ord(list[-1]) < 32:
                    list[-1] = chr(ord(list[-1]) + 95)
            else: list.append(char)
        self.charlist = list
        self.text = ''
        for x in list: self.text += x

    def encode(self):
        list = []
        i = 0
        for char in "redshirt2": list.append(char)
        for char in self.charlist:
            if ord(char) > 32:
                i += 1
                i %= 16
                list.append(chr(ord(char) + self.__table__[i] % 256))
                if ord(list[-1]) < 32:
                    list[-1] = chr(ord(list[-1]) + 160)
            else: list.append(char)
        self.charlist = list
        self.text = ''
        for x in list: self.text += x

```

---

### Post by farnsworth on 2005-06-24
as promised.  just slap it in your .darwinia/full/users/~whoever directory and cheat away.

```

import pygtk
import gtk
import sys

"""
encrypts/ decrypts redshirt2 files
"""

class Redshirt:

    __table__ = [31, 7, 9, 1, 11, 2, 5, 5, 3, 17, 40, 12, 35, 22, 27, 2]
    
    def __init__(self, filename):
        file = PrivoxyWindowOpen(filename, 'rb')
        self.text = file.read()
        file.close()

    def save(self, filename):
        file = PrivoxyWindowOpen(filename, 'w')
        file.write(self.text)
        file.close()

    def decode(self):
        string = ''
        i = 0
        self.text = self.text[9:]
        for char in self.text:
            if ord(char) > 32:
                i += 1
                i %= 16
                char = ord(char) - self.__table__[i]
                if char < 32:
                    string += chr(char + 95)
                else: string += chr(char)
            else: string += char
        self.text = string

    def encode(self):
        string = ''
        i = 0
        string += 'redshirt2'
        for char in self.text:
            if ord(char) > 32:
                i += 1
                i %= 16
                char = (ord(char) + self.__table__[i]) % 256
                if 162 > char > 127:
                    char -= 95
                if char < 32:
                    string += chr(char + 160)
                else: string += chr(char)
            else: string += char
        self.text = string

"""
a textpad
"""
class Textpad(gtk.VBox):

    def __init__(self):
        gtk.VBox.__init__(self, False, 0)
        scrollwin = gtk.ScrolledWindow()
        scrollwin.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        scrollwin.set_size_request(300, 500)
        textview = gtk.TextView()
        self.textbuffer = textview.get_buffer()
        scrollwin.add(textview)
        scrollwin.show()
        textview.show()

        dec_button = gtk.Button("_decrypt")
        enc_button = gtk.Button("_encrypt")
        sav_button = gtk.Button("_save")

        dec_button.connect("clicked", self.decode)
        enc_button.connect("clicked", self.encode)
        sav_button.connect("clicked", self.save)

        buttonbox = gtk.HBox(False, 0)
        buttonbox.pack_start(dec_button)
        buttonbox.pack_start(enc_button)
        buttonbox.pack_start(sav_button)

        self.pack_start(buttonbox)
        buttonbox.show_all()
        
        self.pack_start(scrollwin)

        hbox = gtk.HBox(False, 0)

        self.pack_start(hbox)
        hbox.show()

    def decode(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.decode()
        self.set_text(rs.text)
        self.textbuffer.set_modified(False)

    def encode(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.encode()
        self.set_text(rs.text)
        self.textbuffer.set_modified(False)

    def save(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.save(FILE_NAME)

    def get_text(self):
        start = self.textbuffer.get_start_iter()
        end = self.textbuffer.get_end_iter()
        return str(self.textbuffer.get_text(start, end))

    def set_text(self, text):
        self.textbuffer.set_text(unicode(text, 'latin-1'))
        self.textbuffer.set_modified(False)

if __name__ == "__main__":
    window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    window.set_name("darwinian cheating prog")
    FILE_NAME = sys.argv[1]
    rs = Redshirt(FILE_NAME)
    tp = Textpad()
    window.add(tp)
    tp.show()
    window.set_resizable(False)
    window.connect("destroy", lambda w: gtk.main_quit())
    window.show()
    tp.set_text(rs.text)
    gtk.main()


```

edit: figured you might not want to edit the script for each file.
>>> USAGE: ~$ python redshirt2.py game.txt

edit again: If you see a PrivoxyWindowOpen(), just change it to open().
Privoxy's great, but it can be annoying at times.

edit a third time: dammit.  sys should be imported implicitely.  think I'll have a little chat with Guido.

edit a fourth time: knocked it up a notch.  BAM!

{sigh}: finished 100% a-ok, I think.  I just gave myself a new game with 100% techs!

---

### Post by Adrian_b on 2005-06-25
[QUOTE=farnsworth]as promised.  just slap it in your .darwinia/full/users/~whoever directory and cheat away.

```

import pygtk
import gtk

"""
encrypts/ decrypts redshirt2 files
"""

class Redshirt:

    __table__ = [31, 7, 9, 1, 11, 2, 5, 5, 3, 17, 40, 12, 35, 22, 27, 2]
    
    def __init__(self, filename):
        file = open(filename, 'rb')
        self.text = file.read()
        file.close()

    def save(self, filename):
        file = open(filename, 'w')
        file.write(self.text)
        file.close()

    def decode(self):
        string = ''
        i = 0
        self.text = self.text[9:]
        for char in self.text:
            if ord(char) > 32:
                i += 1
                i %= 16
                char = ord(char) - self.__table__[i]
                if char < 32:
                    string += chr(char + 95)
                else: string += chr(char)
            else: string += char
        self.text = string

    def encode(self):
        string = ''
        i = 0
        string += 'redshirt2'
        for char in self.text:
            if ord(char) > 32:
                i += 1
                i %= 16
                char = (ord(char) + self.__table__[i]) % 256
                if char < 32:
                    string += chr(char + 160)
                else: string += chr(char)
            else: string += char
        self.text = string

"""
a textpad
"""
class Textpad(gtk.VBox):

    def __init__(self):
        gtk.VBox.__init__(self, False, 0)
        scrollwin = gtk.ScrolledWindow()
        scrollwin.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        scrollwin.set_size_request(300, 500)
        textview = gtk.TextView()
        self.textbuffer = textview.get_buffer()
        scrollwin.add(textview)
        scrollwin.show()
        textview.show()

        dec_button = gtk.Button("_decrypt")
        enc_button = gtk.Button("_encrypt")
        sav_button = gtk.Button("_save")

        dec_button.connect("clicked", self.decode)
        enc_button.connect("clicked", self.encode)
        sav_button.connect("clicked", self.save)

        buttonbox = gtk.HBox(False, 0)
        buttonbox.pack_start(dec_button)
        buttonbox.pack_start(enc_button)
        buttonbox.pack_start(sav_button)

        self.pack_start(buttonbox)
        buttonbox.show_all()
        
        self.pack_start(scrollwin)

        hbox = gtk.HBox(False, 0)

        self.pack_start(hbox)
        hbox.show()

    def decode(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.decode()
        self.set_text(rs.text)
        self.textbuffer.set_modified(False)

    def encode(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.encode()
        self.set_text(rs.text)
        self.textbuffer.set_modified(False)

    def save(self, *kwargs):
        if self.textbuffer.get_modified(): rs.text = self.get_text()
        rs.save('game.txt')

    def get_text(self):
        start = self.textbuffer.get_start_iter()
        end = self.textbuffer.get_end_iter()
        return str(self.textbuffer.get_text(start, end))

    def set_text(self, text):
        self.textbuffer.set_text(unicode(text, 'latin-1'))
        self.textbuffer.set_modified(False)

if __name__ == "__main__":
    window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    window.set_name("darwinian cheating prog")
    rs = Redshirt('game.txt')
    tp = Textpad()
    window.add(tp)
    tp.show()
    window.set_resizable(False)
    window.connect("destroy", lambda w: gtk.main_quit())
    window.show()
    tp.set_text(rs.text)
    gtk.main()


```[/QUOTE]
 Is the game worth buying?, it looks all funny and wicked, but an RTS? Oo
You have no gui or anything (=>Age of Empires menu where you select building options and all)
I have played Uplink from Introversion and i know they produce good games, but i can't really poll this one  ](*,)

---

### Post by farnsworth on 2005-06-25
download the demo if you're not sure about it.  I personally love the game.  it's native, runs pretty well, and the built-in editor makes it easy to create your own levels and mods.

---

