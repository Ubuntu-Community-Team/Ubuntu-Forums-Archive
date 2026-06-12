---
title: "comparing content of two folders including all subfolders"
date: 2008-10-01
forum: Desktop Environments
---

### Post by julien-1993 on 2008-10-01
Hi there,
I am facing a situation where I have 2 folders containing thousands of jpeg pictures.

One of them is a prior attempt of me to classified the content of the one that has all the pictures.
To summarize i have lets say folder A that contain 5000 pictures in a lot of sub-folder and sub-sub-folder and i have Folder B that contains about 3000 picture copied from folder A but nicely classified under appropriate sub-folder.

I am looking for a convenient way to compare the content of folder A and B (looking in all the sub-folders of course) and offer me the possibility to copy the file that are in A and not B to another directory to continue my classification.

thank you very much
a guy that is lost in the folders

edit: of course all files have different names, which is the sequence number the camera gives them

---

### Post by skullmunky on 2008-10-02
In KDE there's Komparator, not sure how in Gnome.

I figure this is something i've either needed to do before or surely will, so I whipped up a little python script.  You might try setting up a few test folders with just a few images before running it on the whole shebang :)

It assumes your folders are "Photos" , "Photos-Sorted" , and "SortThese".  Save this script in your home directory as "photosorter.py" and run it from the terminal like this:

```

python photosorter.py

```

```

import os

SortingDirectory = "SortThese"
DirectoryA = "Photos"
DirectoryB = "Photos-Sorted"


# A function to tell if a file counts as an image, by extension
def IsImage(f):
	(shortname,ext) = os.path.splitext(f)
	if ext in ('.jpg','.JPG','nef','.NEF','.JPEG','.jpeg'):
		return True
	else:
		return False
	
	
# main program starts here

treelist1 = {}
treelist1[DirectoryA]=[]

fin,fout = os.popen4 ("ls -R1 " + DirectoryA)
filelist1=fout.read()
files1 = filelist1.splitlines()

fin,fout = os.popen4 ("ls -R1 " + DirectoryB)
filelist2=fout.read()
files2 = filelist2.splitlines()

curdir=DirectoryA

for f in files1:
	if '/' in f:
		curdir=f
		curdir=curdir.rstrip(':')
		treelist1[curdir]=[]
	else:
		# only add files with matching extensions
		if IsImage(f):
			treelist1[curdir].append(f)


print "Files that are in Photos and not in Photos-Sorted"
for d in treelist1:
	for f in treelist1[d]:
		if not f in files2:
			print f

# do the same traversal, but copy them
for d in treelist1:
	for f in treelist1[d]:
		if not f in files2:
			cmd='cp "' + d + '/' + f + '" ' + SortingDirectory
			os.system(cmd)

```

---

