---
title: "Bulk renaming using a spreadsheet or CSV"
date: 2009-02-14
forum: General Help
---

### Post by WunderSlug on 2009-02-14
I'm at my wits end after searching for approx. 4 hours now.

I need to rename about 13000 images from their original name to match a product code.

I have a spreadsheet with the original names in column A and need them to be renamed to the product codes that are in column B.

Example:

Column A          Column B
blah4567.jpg  8792235.jpg
trdfg2354.jpg  638743.jpg
aqwer6.jpg    367543.jpg

and so on.

I have been searching for a bulk rename tool, or a script, but nothing seems to match up to what I need.  Everything I come across is for partial name replacement or a DOS command.

Can anybody help?
Thank you in advance.

(Whoops! Sorry for the crappy formatting in the example!)****

---

### Post by WunderSlug on 2009-02-14
I hate to do this...bump.

---

### Post by amauk on 2009-02-14
assuming all these images are in the same directory, and the spreadsheet is saved as comma separated values (CSV)

**Untested** - you may want to do a dry run on a small sub-set of files before doing the full run

```
#!/bin/bash

# Variables, edit to suit
IMG_DIR="/path/to/images"
CSV_FILE="/path/to/spreadsheet.csv"

# script start

# separate on newlines only
IFS=$'\n'

# Loop all lines in CSV
CSV_LINES=($(cat "$CSV_FILE"))
for CSV_LINE in ${CSV_LINES[@]}
do
	OLD_NAME=`echo "$CSV_LINE" | grep -o '^"[^"][^"]*"' | sed 's/"//g'`
	NEW_NAME=`echo "$CSV_LINE" | grep -o '"[^"][^"]*"$' | sed 's/"//g'`
	
	# continue only if old file actually exists
	if [ -f "$IMG_DIR/$OLD_NAME" ];
	then
		# continue only if new filename given
		if [ -n "$NEW_NAME" ];
		then
			mv "$IMG_DIR/$OLD_NAME" "$IMG_DIR/$NEW_NAME"
		fi
	fi
done

IFS=$' \t\n'
```

---

### Post by WunderSlug on 2009-02-14
well, I have to admit, I don't know a whole hell of a lot about scripting.  But from what I read, that seems like it would do the trick.

I'll give it a whirl on a couple copied images and see what happens.


Thanks !

---

### Post by geirha on 2009-02-14
If you save that spreadsheet as csv, it should look like this:
```

"blah4567.jpg","8792235.jpg"
"trdfg2354.jpg","638743.jpg"
"aqwer6.jpg","367543.jpg"

```

One thing you can do is to simply turn it into a shell-script:
```

echo '#!/bin/sh' > rename-images.sh
sed 's/","/" "/;s/^/mv -v /' file.csv >> rename-images.sh

```
If any of the files contain a quotation mark " it will fail for those files, but it's unlikely that any files contain a quotation mark.

The sed first replaces «","» with «" "», and then adds «mv -v » to the start of each line.
The resulting rename-image.sh should look like:
```

#!/bin/sh
mv -v "blah4567.jpg" "8792235.jpg"
mv -v "trdfg2354.jpg" "638743.jpg"
mv -v "aqwer6.jpg" "367543.jpg"

```

Try it on a copy of the images (please keep a backup around in case it doesn't work out as expected)
```
sh rename-images.sh
```

---

### Post by WunderSlug on 2009-02-14
I tried the second suggestion and it seemed to work except that I got this error:

mv: missing destination file operand after `SADfsadfg34.jpg,31206'


any thoughts?

edit:  actually the resulting .sh doesn't have the quotes or the .jpg extension around the target filenames.

wonder why?

---

### Post by geirha on 2009-02-14
Could you post an example of how the csv-file looks? I created the csv file by creating an open office spreadsheet with the values you posted, then saved it as csv, and chose the default options, which was " around strings and , as separator.

---

### Post by WunderSlug on 2009-02-14
copied straight from the csv

"51tan.jpg",37999
"51white.jpg",37991
"51blacks.jpg",38009
"512blacks.jpg",38010
"51green.jpg",38034
"5116green.jpg",38033

---

### Post by geirha on 2009-02-14
Ah I see, the second column actually contains numbers instead of filenames.
Try with this modification of the sed:
```
echo '#!/bin/sh' > rename-images.sh
sed 's/",/" /;s/^/mv -v /;s/$/.jpg/' file.csv >> rename-images.sh
```

EDIT: Looking more closely at it, this will also fail for files that start with a , ... not very common to have a file start with , though.

---

### Post by WunderSlug on 2009-02-14
holy crap...IT WORKED!!!


I have been trying to do this for WEEKS!

I can't THANK YOU enough!!!!!!!!!!!!!!!

---

### Post by ByteJuggler on 2009-02-14
Out of interest, here's an "awk" solution.  One line only.  :)

```
cat test.csv | awk 'BEGIN { FS=","; print "#!/bin/bash" }   { printf("mv %s \"%s.jpg\"\n", $1,  $2) } ' | bash
```

If you want to see the output use:

```
cat test.csv | awk 'BEGIN { FS=","; print "#!/bin/bash" }   { printf("mv %s \"%s.jpg\"\n", $1,  $2) } ' > rename.sh
```

... and then view rename.sh.

---

### Post by WunderSlug on 2009-02-14
yup...just renamed about 5000 as a test...still can't believe it...


Thank you so much

---

