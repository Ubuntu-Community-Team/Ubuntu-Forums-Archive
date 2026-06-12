---
title: "Creating a universal repo for a specific program?"
date: 2009-05-13
forum: General Help
---

### Post by Buttons840 on 2009-05-13
I want to create a local repository which I can use on computers without internet connections.  All the computers could potentially have different configurations.

Is there an easy way to download a program and ALL its dependencies, so that I could install it on any computer?  (When I say any computer, I mean any computer with the ability to use the repo.)

Let's say I want a repository with ProgX in it, along with all possible dependencies.  I could run apt-get install ProgX -d and it would download ONLY those packages that are not already installed.  I would like it to download ALL dependencies, because there is no guarantee that the next computer is going to have the same packages pre-installed.  Preferably, it will put all these downloaded .deb's into a specified folder.

In short, is there a way to download .deb packages and make a repository which will fulfill all potential dependency requirements on any computer configuration?

My current idea is to do a fresh install, which will include many many packages, but no .deb's.  I will select all installed packages in synaptic and mark for re-installation, and then download only the .deb's.  This way I will have all the .deb's including in the fresh distribution, and I will have all my bases covered.  I can then download the programs I want, synaptic will automatically grab any missing dependencies, and I can package everything together into a local repository.  There will be many redundant .deb's which are included with the distro, but not needed by the programs.

Any advice is appreciated.

---

### Post by KhurramM on 2009-05-13
See the man of apt

u can store all the downloaded debs

further, make a clean Cd install on one PC.

Start installing via apt and saving debs

U wont have to repeat this for other PCs

all the dependencies will be fulfilled.

Hope this helps u

---

### Post by mac9416 on 2009-05-13
If for any reason you need to use an OS besides Debian/Ubuntu to download the .debs you should use [Keryx]("http://keryxproject.org"). Even if you're on Ubuntu, it makes downloading the packages with dependencies a lot easier.
    If you use Keryx to download the software I have written a python script that will turn any Keryx project into a .deb repository. To use it:
[LIST=1]
[*]Use Keryx to download your software
[*]Copy my script as "quickrepo.py" into your Keryx project
[*]Run the script on the command line (it could take a few minutes to run, but you will know it's doing something)
[*]When it's finished, there will be another folder in your Keryx project directory called "repo_name" This is your software repository.
[*]Add the local repository to your sources.list (ex. file:///home/nickaname/repo_name/ Jaunty universe etc.)
[/LIST]

It's complicated, I know. But I once you have [Keryx]("http://keryxproject.org") and have used it, you can PM me and I'll help you with making the repo.
Here's the code for the repo-maker:
```
import os, os.path, shutil
from gzip import GzipFile

REPO_NAME = 'repo_name'
repodir = os.path.join(os.getcwd(), REPO_NAME)

listdir   = os.path.join(os.getcwd(), 'lists')
packdir   = os.path.join(os.getcwd(), 'packages')
if not os.path.exists(listdir):
    print "There is somethin' wrong with you, son! You don't even have a ./lists directory. Make sure that you are running this script from within an Ubuntu-type Keryx project.'"
if not os.path.exists(packdir):
    print "What's this?! I can't find a ./packages directory. Make sure that you are running this script from within an Ubuntu-type Keryx project."
listfiles = os.listdir(listdir)
packfiles = os.listdir(packdir)

def stripDotCom(text, prefix=''):
    append = False
    final = ''
    for item in text.split('_'):
        if item == 'dists':       append = True
        if append:
            final = os.path.join(final, item)
    return os.path.join(prefix, final)

def convertUnderscores(text, prefix): # Returns a file that has converted underscores ("_") to / or \ in a filename.
    final = ''
    for item in text.split('_'):
        final = os.path.join(final, item)
    return os.path.join(prefix, final)

def splitPacks(text, filenameprefix):
    filename = ''
    packs = {}
    for block in text.split('\n\n'):
        for line in block.split('\n'):
            if line.startswith('Filename: '):
                filename = line[10:]
        if filename != '':
            packs.update({os.path.abspath(os.path.join(filenameprefix, filename)):block})
    return packs

count = 0
lists = {}
for filename in listfiles:
    try:
        listfile = open(os.path.join(listdir, filename), 'rb')
    except:
        print "Well, that list just wouldn't load: " + filename
        continue
    packs = splitPacks(listfile.read(), repodir) # splitPacks returns {packfilename:packtext, etc.}
    listfile.close()
    if lists.has_key(stripDotCom(filename, repodir)):       # If a list located in the same part of the repo has already been scanned...
        lists[stripDotCom(filename, repodir)].update(packs) # Simply add the current data to that file.
    else:                                                   # Else...
        lists.update({stripDotCom(filename, repodir):packs})# Add the new list!
    count += 1
    print count, "read of", len(listfiles)

for packlist in lists.iteritems():
    packlisttext = ""
    for pack in packlist[1].iteritems():
        if os.path.split(pack[0])[-1] in packfiles: # If the file from the index file is in the packages directory...
            packlisttext += (pack[1] + '\n\n')      # Add this to the new index file,
            if not os.path.exists(pack[0]):         # Then copy the deb into the repo.
                try: os.makedirs(os.path.dirname(pack[0]))
                except: pass
            print "Copying " + os.path.split(pack[0])[-1] + "..."
            shutil.copy(os.path.join(packdir, os.path.split(pack[0])[-1]), pack[0])
    if not os.path.exists(packlist[0]): 
        try: os.makedirs(os.path.dirname(packlist[0]))
        except: pass
    print "Writing file: " + packlist[0] + '.gz'
    packlistfile = file(packlist[0] + '.gz', 'wb')
    gzfile = GzipFile(packlist[0], 'wb', 9, packlistfile)
    gzfile.write(packlisttext)
    gzfile.close()
    packlistfile.close()
```

---

### Post by Buttons840 on 2009-05-13
Keyrx is a good solution for a single computer, but I want to make universal repositories that will work on *any* computer (assuming it has a compatible package manager).  I just want a more universal solution.

From my understanding Keyrx is best suited for updating a specific computer?  Or at least computer that are very similar.  I appreciate the help though, and I'm open to new information about Keyrx.  Perhaps I do not fully understand it?

Right now my solution is to do a fresh install using a virtual machine.  From there I will download debs for *all* installed packages using synaptic.  I will then download the additional programs I desire, and then package everything up.  I also got apt-proxy installed and working, which makes me happy.  It's nice to not have to download the same thing over and over from the repositories every time I try a new VM.

Further advice is still welcome.

---

### Post by EXCiD3 on 2009-05-13
For Keryx you create a project for a specific computer and use that to gather packages. This will download dependencies based upon the installed packages for that computer. If you have a computer that is a fresh install, downloading the packages for that project would have all the dependencies for another computer even if it had new packages installed on it already. You can then add those packages to a local repo and install from there or whatever you like.

I would suggest creating a project from a fresh install and then just using that. It works the same way as the virtual machine route, only much less hassle. :)

---

