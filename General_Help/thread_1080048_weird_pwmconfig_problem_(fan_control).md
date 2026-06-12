---
title: "weird pwmconfig problem? (fan control)"
date: 2009-02-25
forum: General Help
---

### Post by sojojo on 2009-02-25
Hey, I tried to set up some fan control for my Abit NF-M2 nView motherboard using pwmconfig (as per [this thread]("http://ubuntuforums.org/showthread.php?t=42737")), however its having some issues. I know it can do fan control based on my Windows experiences with it. When I run pwmconfig and it comes to testing, none of the fans turn off. Essentially everything is running at 100% and its too loud!! My only clue right now is this error message when I try to set the min pmw for the cpu fan. it reads: ```
Setting  to 10.../usr/sbin/pwmconfig: line 583: $pwms: ambiguous redirect

```
i looked in gedit at /usr/sbin/pwmconfig, and this is the function: ```
function TestMinStart {
	echo
	echo 'Now we increase the PWM value in 10-unit-steps.'
	echo 'Let the fan stop completely, then press return until the'
	echo "fan starts spinning. Then enter 'y'."
	echo 'We will use this value +20 as the starting speed.'
	let fanok=0
	let fanval=0
	until [ "$fanok" = "1" ]
	do
		let fanval=fanval+10
		if [ $fanval -gt 240 ] ; then let fanval=$MAX ; let fanok=1 ; fi
		echo -n "Setting $pwms to $fanval..."
		echo $fanval > $pwms
		read FANTEST
		if [ "$FANTEST" != "" ] ; then let fanok=1 ; fi
	done
	let fanval=fanval+20
	if [ $fanval -gt 240 ] ; then let fanval=$MAX ; fi
	echo "OK, using $fanval"
	echo $MAX > $pwms
}
```
line 583 is "echo $fanval > $pwms" 
I just have 2 fans right now, a big *** zalman (don't remember what its called) plugged into the cpu fan port, and a regular 120mm Yate Loon fan up front plugged into AUX.
Any ideas?? I have all the output from sensors, if thats helpful too. None of the temps are out of the ordinary or anything, although some of the voltages look a little off. Anyway.. Thanks!

---

