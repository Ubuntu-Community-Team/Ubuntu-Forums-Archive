---
title: "scrolling around using touchpad can sometimes causes url to be clicked"
date: 2014-07-13
forum: Desktop Environments
---

### Post by mctiew on 2014-07-13
I am using Ubuntu LTS 14.04 running compiz.

I am also using firefox version 30.

I don't know what's the cause of problem, sometimes when I just move around the firefox output using the touchpad ( such as scroll up/down/left/right ), some url got clicked and some part of the text get to be come highlighted (as thought in a mouse copy operation). 

Here is my synclient output :-

> 
$ synclient 
Parameter settings:
    LeftEdge                = 300
    RightEdge               = 1700
    TopEdge                 = 210
    BottomEdge              = 1190
    FingerLow               = 12
    FingerHigh              = 15
    MaxTapTime              = 180
    MaxTapMove              = 107
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 141
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 48
    HorizScrollDelta        = 48
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0819336
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 100
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 15
    PressureMotionMaxZ      = 80
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 0
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 12
    VertHysteresis          = 12
    ClickPad                = 0



Maybe some setting not right with the touchpad settings ?

---

### Post by Vladlenin5000 on 2014-07-13
> **mctiew said:**
> I am using Ubuntu LTS 14.04 running compiz.

I am also using firefox version 30.

I don't know what's the cause of problem, sometimes when I just move around the firefox output using the touchpad ( such as scroll up/down/left/right ), some url got clicked and some part of the text get to be come highlighted (as thought in a mouse copy operation). 

Here is my synclient output :-



Maybe some setting not right with the touchpad settings ?

If anything then it's sensitivity.
Your 'symptom' is consistent with a one-finger tap (=> left-click) or one-finger tap&hold (=> left-click&hold).

---

### Post by mctiew on 2014-07-13
I saw some posts that I could set 'synclient MaxTapTime=0' to disable tap to click.

It's quite a nuisance to me, so I am disabling it to see if it helps.

---

