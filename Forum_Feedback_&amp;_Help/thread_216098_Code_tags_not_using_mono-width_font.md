---
title: "Code tags not using mono-width font"
date: 2006-07-14
forum: Forum Feedback &amp; Help
---

### Post by jayemef on 2006-07-14
I just noticed that the code tags are nolonger using a mono-width font. Can this be looked into?

```
1234567890   # This line should line up
..........   #+with this one.
```

Thank you

---

### Post by oldmanstan on 2006-07-15
i sorta like the new font, i'm not a big fan of mono-width for code, i find it hard to read, but i see the point

maybe make it optional?

---

### Post by jayemef on 2006-07-15
Are you a coder? Not using a mono-width font makes it nearly impossible to produce visually clean code. Take the first few lines from a project I had been working on for fun about a year ago:

```

public class SudokuCell {

    private int   _value;          // Value of the cell. Use zero if empty.
    private int   _num_candidates; // Number of current candidates.
    private int[] _candidates;     // Possible candidate values for the cell.

```

Likewise, look at some of the documentation within it:
```

  --CONVENTIONS--
  cell:            + An individual element/square in a sudoku puzzle.
  row:             + A horizontal 1x9 grouping of cells in a sudoku puzzle.
                     Rows are numbered 0-8, going from top to bottom.
  col/column:      + A vertical 9x1 grouping of cells in a sudoku puzzle. Cols
                     are numbered 0-8, going from left to right.
  box:             + A box is a 3x3 grouping of cells in a sudoku puzzle. Boxes
                     are numbered 0-8, starting at the top left of the puzzle
                     and readling from left to right.
  unit:            + A generic name for either a row, column, or box. 

```

or for another example:
```

$months_of_the_year = array(
    "January"   => 1,
    "February"  => 2,
    "March"     => 3,
    "April"     => 4,
    "May"       => 5,
    "June"      => 6,
    "July"      => 7,
    "August"    => 8,
    "September" => 9,
    "October"   => 10,
    "November"  => 11,
    "December"  => 12
)

```

With a mono-width font, this would be lined up quite nicely in columns, making it very easy to follow (try pasting any of these into gedit or what have you and look at the difference), but instead it's a chore to read. Vertical spacing is extremely important when it comes to source code.

Now one could make the argument that one could just as easily put in extra spaces so that it appears to be lined up, or at least close to it. But this is only useful that person is the only one to ever work with the code. Otherwise, handing the code off to someone else would either require that they use the same font as the giver, which is a no-no as different people will prefer different fonts, and if the reciever is using a mono-width font, that source will look just as sloppy as the examples above.


On the side, what I think would be awesome, is if like the quote tag where you can specify the name of the person you are quoting, it would be great if you could specify the language of the code you are using, ie code=c#, code=python, etc. Then, given that information, the proper syntax could be applied. This may or may not be a pain in the *** to incorporate here, but I'd love it and wouldn't mind taking the time to look into if a desire is felt.

---

### Post by ubuntu-geek on 2006-07-15
I'll be fixing this shortly..

---

### Post by oldmanstan on 2006-07-15
i am not a professional coder but i do know that the stroustrup c++ book uses a non fixed width font for code examples, considering the guy wrote c++ i'd say he knows a thing or two, i think it's just a personal preference thing

if you want things to line up you can just use tabs instead of spaces, like i said, personal perference

---

### Post by jayemef on 2006-07-16
I'm not arguing that preference has nothing to do with it. If you are more comfortable with a non-mono-width font, then more power to you. But objectively, you are just expected to have readable code in any sort of professional setting. I won't deny that you might know some books that print source in an unusual font, but that could always be a limitation of the publisher. In any case, for every book that uses a non-mono-width font, I'm sure you could find hundreds that don't.

Spaces versus tabs are a pretty solid debate though. I lean toward spaces for the simple fact that tabs don't appear identical in every editor in relation to the rest of the document. Widths change from editor to editor, and sometimes tabs align to a ruler rather than always inserting an exact amount of indentation. The same document can look completely different in different editors. Spaces avoid this complication by keeping it all uniform.

So what are the advantages of tabs? They're great for personal preference. Most editors allow you to specify exactly how your tabs behave, so you can have one coder on your team who prefers a 2-width indentation and another who prefers 4. With tabs, they could both operate as they please. In addition, it's one button to press rather than several spaces.

My argument to this though is that a team should really have an agreed-upon style that everyone will use. Yes, I prefer K&R bracketing, but if I'm in a group of 10 coders and the other 9 prefer something else, I'll use that instead. With uniform, selfless code, anyone should be able to pick up any part of the project and be able to read/edit/add/etc. Spaces keep indentation uniform, and if a particular coder is really big on tabs, most editors allow you to change the tab behavior to instead insert x number of spaces.

Finally, going back to the original argument, if for nothing else the code block should be looked into simply because as it stands now, I *believe* it is essentially identical to the quote block. No sense in having two identical options.


@ubuntu-geek: Thanks for looking into this. I really appreciate it.

---

### Post by oldmanstan on 2006-07-16
ok, well i hadn't really thought about the fact that the code block and quote block were identical, so that makes perfect sense to change the code block since mono-width makes more sense for many people.

i do see your points, just my opinion (easy for me to have since i don't have to do it for a living)

---

