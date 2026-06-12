---
title: "Nautilus: branch view of folders?"
date: 2010-11-05
forum: Desktop Environments
---

### Post by Optimus Yarnspinner on 2010-11-05
Hi, is there any quick and easy way in Nautilus to show all files of a folder, no matter how deeply they are stored within its subfolders? 

As an attempt to visualize, let's assume I have a folder F, containing two files and two subfolders, which each contain one file.
```
<F>
+-file1
+-file2
+-<subf1>
 +-file3
+-<subf2>
 +-file4
```Is there any quick hotkey, or buttonclick that can give me a branch view (without actually moving the files out of the subfolders yet)? Example:
```
<F>
+-file1
+-file2
+-file3
+-file4
```.

Thanks in advance

---

### Post by Optimus Yarnspinner on 2010-11-06
An actual application could be:

I have a folder structured like this:

```
<F>
+-<CD1>
 +-track1
 +-track2
 +-track3
+-<CD2>
 +-track1
 +-track2
 +-track3
+-<CD3>
 +-track1
 +-track2
 +-track3

```

and I want to pull out the files from the subfolders and have them in the main folder. Usually I'd have to go into each subfolder and manually rename each of the 9 files to avoid filename collision. That procedure would take me at least 15 steps (9 renames, 3x open folder, 3x go to parent folder)

Now if I had a branchview command that just displayed all files in <F>, I would get:

```
 <F>
+-track1
+-track[FONT=Verdana]1[/FONT]
+-track1
+-track2
+-track2
+-track2
+-track3
+-track3
+-track3
```

Next, if I had some bulk renaming GUI, I could select them all and set the new filename to [parentfolder] + [original filename], so I get (still in branch view)
```
 <F>
+-CD1 track1
+-CD1 track[FONT=Verdana][FONT=monospace]2[/FONT][/FONT]
+-CD1 track3
+-CD2 track1
+-CD2 track2
+-CD2 track3
+-CD3 track1
+-CD3 track2
+-CD3 track3 
```
Then I could just select the lot, cut, and go back to normal view, then insert, and I have 
```
 <F>
+-<CD1>
+-<CD2>
+-<CD3>
+-CD1 track1
+-CD1 track[FONT=Verdana][FONT=monospace]2[/FONT][/FONT]
+-CD1 track3
+-CD2 track1
+-CD2 track2
+-CD2 track3
+-CD3 track1
+-CD3 track2
+-CD3 track3 
```
Just so you get my idea. If it really cannot be done in Nautilus, I&#7743; also open for suggestions concerning other filemanagers :)

---

### Post by Optimus Yarnspinner on 2010-11-08
Bump, would love a quick hotkey that changes between normal folder view and a flattened branch view. Or a hint for a way to get it working :)

---

