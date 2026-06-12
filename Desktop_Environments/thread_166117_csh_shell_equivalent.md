---
title: "csh shell equivalent"
date: 2006-04-25
forum: Desktop Environments
---

### Post by frogotronic on 2006-04-25
Hello,

  I'm trying to get IMAGE 3.10 ([http://www.sanger.ac.uk/Software/Image/]("http://www.sanger.ac.uk/Software/Image/")) to run on UBUNTU BB.  It's a programme to analyse DNA fingerprint gels for use in FingerPrint Contig (FPC); another LINUX based programme.  I've got it pretty much set up, BUT there is a script that automates a complicated import of the initial data that isn't working.  My understanding is the people at the Sanger centre used RED HAT which uses a 'csh' shell.  I've tried 'tcsh'; but the programme still crashes.

_Here's the error message:_

bash: /usr/local/bin/import: /bin/csh: bad interpreter: Permission denied

I'm not very comfortable in linux/UBUNTU so any explanation needs to be couched in lay terms (assuming a high level understanding of MS Windows O/S systems).

Thanks in advance

_Here's the script that I'm trying to run: _

#!/bin/csh -f
# $id$
#
# Authors: F. Wobus, D. Platt.
#

if ( $#argv != 3 ) then
	echo "Usage: imimport <project> <gelname> <imagefile>"
	echo "       ... creates a gel project with an existing image file"
	exit 1
endif

if (`echo "$IMTOP_DIR" | wc -c` <= 1) then
	echo 'ERROR :  $IMTOP_DIR'" isn't set, please setenv first, for example ~/imdata"
	exit 1
endif

set project = $1
set gel = $2

# create subdirs if they don't already exist
if (! -d $IMTOP_DIR) then
	mkdir $IMTOP_DIR
endif
if (! -d $IMTOP_DIR/$project) then
	mkdir $IMTOP_DIR/$project
endif
if (! -d $IMTOP_DIR/$project/INCOMING) then
	mkdir $IMTOP_DIR/$project/INCOMING
endif

if (! -d $IMTOP_DIR/$project/INCOMING/$gel) then
	mkdir $IMTOP_DIR/$project/INCOMING/$gel
endif

# determine the format by getting the file extension
set format = $3:e

if ($format == 'GIF') then
  #
  # GIF file from the PC might have an uppercase file extension
  #
  set format = "gif"
else if ($format == 'tiff' || $format == 'TIF' || $format == "TIFF" || $format == "GEL" || $format == "gel") then
  #
  # TIFF files might end in also in tiff, as well as TIF or TIFF when transfered from a PC
  # FluorImager 16 bit image files will end in GEL or gel, they are also tif's.
  #
  set format = "tif"
endif

#
#check for a valid format
#
if (!($format == 'hi' || $format == 'dat' || $format == 'gif' || $format == 'tif' || $format == 'abi')) then
  #
  # no valid format, reset the $format variable
  #
  set format = ""
  #
  # loop through the input loop until a valid extension has been entered
  #
  while ($format == "")
    echo    "Please specify the image type"
    echo -n ' enter one of "hi", "dat", "gif", "tif", "abi" or "q" to abort : '
    set format = $<
    if ($format == 'Q' || $format == 'q') then
       echo ""
       echo "Exit ..."
       exit 1
    else if (!($format == 'hi' || $format == 'dat' || $format == 'gif' || $format == 'tif' || $format == 'abi')) then
       set format = ""
    endif
  end
endif

set dest = $IMTOP_DIR/$project/INCOMING/$gel/image.$format

#
# We also need to import the mac resource file if we are dealing with
# an ABI file.  It could be in one of three places.
# %gelfile .rsrc/gelfile .resource/gelfile
#
if ($format == 'abi') then
	#
	# Search for the different kinds of resource.
	#
	set gelName = `basename $3`
	set gelDir = `dirname $3`
	set resFile1 = $gelDir/%$gelName
	set resFile2 = $gelDir/.rsrc/$gelName
	set resFile3 = $gelDir/.resource/$gelName
	set resFile4 = $gelDir/.AppleDouble/$gelName
	set resFile5 = $gelDir/${gelName}.res
	#
	# Test for the different resources.
	#
	set found = false
	if ( -f $resFile1) then
		echo "Apple double resource format"
		echo "cp $resFile1 $IMTOP_DIR/$project/INCOMING/$gel/%image.abi"
		cp $resFile1 $IMTOP_DIR/$project/INCOMING/$gel/%image.abi
		set found = true
	else if ( -f $resFile2) then
		echo "Ethershare resource format"
		echo "mkdir $IMTOP_DIR/$project/INCOMING/$gel/.rsrc"
		mkdir $IMTOP_DIR/$project/INCOMING/$gel/.rsrc
		echo "cp $resFile2 $IMTOP_DIR/$project/INCOMING/$gel/.rsrc/image.abi"
		cp $resFile2 $IMTOP_DIR/$project/INCOMING/$gel/.rsrc/image.abi
		set found = true
	else if ( -f $resFile3) then
		echo "CAP resource format"
		echo "mkdir $IMTOP_DIR/$project/INCOMING/$gel/.resource"
		mkdir $IMTOP_DIR/$project/INCOMING/$gel/.resource
		echo "cp $resFile3 $IMTOP_DIR/$project/INCOMING/$gel/.resource/image.abi"
		cp $resFile3 $IMTOP_DIR/$project/INCOMING/$gel/.resource/image.abi
		set found = true
	else if ( -f $resFile4) then
		# Babelfish produces a .AppleDouble/$gelName
                # rather than a %$gelName but the format is the same
                echo "Apple double resource format (Babelfish)"
		echo "cp $resFile4 $IMTOP_DIR/$project/INCOMING/$gel/%image.abi"
		cp $resFile4 $IMTOP_DIR/$project/INCOMING/$gel/%image.abi
		set found = true
	else if ( -f $resFile5) then
		echo "Gelmover format"
		echo "cp $resFile5 $IMTOP_DIR/$project/INCOMING/$gel/image.abi.res"
		cp $resFile5 $IMTOP_DIR/$project/INCOMING/$gel/image.abi.res
		set found = true
	else
		echo "ERROR - couldn't find a mac resource file."
		echo $resFile1
		echo $resFile2
		echo $resFile3
		echo $resFile4
		echo $resFile5
		exit 1
	endif
	if ($found == 'true') then
		echo "uncanres $dest"
		uncanres $dest
		ln -s $IMTOP_DIR/$project/INCOMING/$gel/matrix1 $IMTOP_DIR/$project/INCOMING/$gel/matrix
		#
		# uncanres always(?) makes an info file. For im3.10a
                # and higher this confuses image so remove it
		#
		if ( -f $IMTOP_DIR/$project/INCOMING/$gel/info) then
			echo rm -f $IMTOP_DIR/$project/INCOMING/$gel/info
			\rm -f $IMTOP_DIR/$project/INCOMING/$gel/info
		endif
		
		#
		# uncanres could make a lanes file if there was
		# one on the Mac side, so we should remove it
		# because image has its own lanes file
		#
		if ( -f $IMTOP_DIR/$project/INCOMING/$gel/lanes) then
			echo rm -f $IMTOP_DIR/$project/INCOMING/$gel/lanes
			\rm -f $IMTOP_DIR/$project/INCOMING/$gel/lanes
		endif
		
		#
		# Make a time-shifted, clean ABI image from the data
		#
		echo "Cleaning ABI image - removing gaps and time shifting"
		echo ""
		echo "cleanABI $3 $dest"
		cleanABI "$3" $dest

		if ( -f $dest) then
			exit 0
		else
			echo "Failed to import clean ABI image - ERROR"
			exit 1
		endif

	endif
endif

echo "cp '$3' '$dest'"
cp "$3" "$dest"

exit 0

---

### Post by taylork on 2006-04-25
sudo apt-get install tcsh

---

### Post by Ptero-4 on 2006-04-25
taylork. I think th OP said that tcsh didn't solve his problems running the script.

---

### Post by frogotronic on 2006-04-25
Hello,

  Nope, doesn't solve the problem.  (I've already tried that).

  I was told (by Sanger Centre) that : [B]"import is c shell script, the firstline of the script is a comment line

#!/bin/csh -f

this contains the path of the program that should be used to interpret the command in this script. It's possible the csh interpreter is missing or located elsewhere in your system. You should edit the imimport script to point to the correct location or you could try changing csh to tcsh if that is available."[/B]

But installing tcsh doesn't help.  I think the script needs editing, or rather I need to know where the "csh" equivalent REDHAT of UBUNTU is located.  This is pretty much where my knowledge of LINUX breaks down - differences between the builds (?).

- Andor

---

### Post by Ptero-4 on 2006-04-26
does apt-get install csh get you something.

---

### Post by 5-HT on 2006-04-26
[quote=cement_head]...installing tcsh doesn't help.  I think the script needs editing, or rather I need to know where the "csh" equivalent REDHAT of UBUNTU is located.  This is pretty much where my knowledge of LINUX breaks down - differences between the builds (?).

- Andor[/quote] 
Hi, have you tried the direct route of installing csh, as Ptero-4 indicated, and running the script?

It's not installed in a default Breezy setup, but is available using a quick ```
sudo apt-get install csh 

OR

sudo aptitude install csh

OR 

via synaptic 
``` 
That should hopefully clear up the interpreter problem.

If not, maybe forcing csh with a ```
csh <path_to_script>
``` may help.

Additionally, csh may not be installing into /bin/csh (however, there is only a very small chance of this happening and it would usually require user intervention). If so, doing a ```
 which csh 
``` will let you know where the executable is, and you could edit the shebang of the script accordingly (from #!/bin/csh to #!<results of 'which csh'>).

Hope you get it working.

---

### Post by frogotronic on 2006-04-26
And the winning solution courtesy of a friend (who works at [NIST]("http://www.nist.gov/")) of a friend is:

**ln -s /bin/tcsh /bin/csh**

Basically, I created an alias so that everytime the script tries to use the csh shell, the tcsh shell is substituted.

---

### Post by taylork on 2006-04-26
sudo update-alternatives --all

or

sudo update-alternatives --auto csh

would have done this for you after you did an apt-get on tcsh. 

Sorry, I thought it would do that for you automatically when it installed tcsh. I guess I don't know when it decides to run it....

---

