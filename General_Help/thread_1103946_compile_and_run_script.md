---
title: "compile and run script"
date: 2009-03-23
forum: General Help
---

### Post by Shady3D on 2009-03-23
i wanted to make a Nautilus script to compile and run c/c++ and c++ with glut and thats what i made so far 
```

#!/bin/sh

###to choose compiler with options
ans=$(zenity  	--list --text "plz, choose a compiler" --radiolist \
				--column "Pick" --column "Compiler" --column "Description" \
				 TRUE "g++ -lglut" "c++ compiler with glut library (openGL)" \
				 FALSE "g++" "c++ compiler" \
				 FLASE "gcc" "c compiler")

###look for the selected compiler and compiles it
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do

	if [ "$ans" = "g++ -lglut" ]; then
		g++ "$FILE" -o "`dirname $FILE`/out" -lglut
		
	elif [ "$ans" = "g++" ]; then
		g++ "$FILE" -o "`dirname $FILE`/out"
		
	elif [ "$ans" = "gcc" ]; then
		gcc "$FILE" -o "`dirname $FILE`/out"
			
	else
		zenity --error --text="you should select one option from the list"
	fi
done

###looks for the compiled program then if it exist it run it
if [ -e "`dirname $FILE`/out" ]; then
	zenity --info --text="program compiled"
	`dirname $FILE`/./out
	rm "`dirname $FILE`/out"
else
	zenity --error --text="couldn't compile the program"
fi

```

**_but i got 3 problems:_**
[LIST=1]
[*]the zenity command doesn't popup ontop of all windows
[*]if a program contains printf it doesn't appear
[*]i wan't to show to errors and warning but i don't know how
[/LIST]

---

