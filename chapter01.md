## _ in interactive mode

In interactive mode, the underscore (_) stores the values of the most recently evaluated expression. 

## "Banker's rounding" with the round function

The round function rounds as expected, except in the case of rounding X.5, where X is an even number. The round function does "banker's rounding", which means it rounds halves to the nearest EVEN integer. Hence:

```
round(0.5) returns 0
round(1.5) returns 2
round(2.5) returns 2
round(3.5) returns 4
round(4.5) returns 4
```

## What logical expressions return

Logical expressions always return one of the operands, rather than True or False. AND returns the first falsey value, or the last one if they are all truthy. OR returns the first falsey value, or the last one if they are all truthy.

| x or y | If x is False y; otherwise x |
| x and y | If x is False x; otherwise y |

The way to think about this is that Python returns the value at which it stopped the lazy evaluation of the expression.

## Reminder about the walrus operator

```
x = 0
while (x := x + 1) < 10:
    print(x)
```

The assignment expression must be enclosed in brackets.

## A reminder about repr

>>> s = 'Hello\nworld'
>>> s
Hello
world
>>> repr(s)
'Hello\nworld'

## Reading a file in chunks

`s = f.read()` reads the whole file into a string, but you can give read a hint as to how much to read with each call:

```
while (chunk := file.read(10_000)):
    print(chunk, end = '')
```

## Printing to a file using print

```
f = open('out.txt', 'r')
print('Hello', file = f)
```
## Set operations

a = t | s # Union 
b = t & s # Intersection 
c = t - s # Difference 
d = s - t # Difference 
e = t ^ s # Symmetric difference

The symmetric difference is the set of items that are in one or the other but not both.

`s.add` Adds a single item.
`s.update` Adds the elements of a set.
`s.remove` and `s.discard` do the same thing, except that `remove` raises an error if the argument is not in s.

## Exiting the program by raising SystemExit

The book suggests that `raise SystemExit()` is the correct way to force the exiting of a Python program. CGPT says that this is indeed correct and that it's what sys.exit() does under the hood. 

`exit()` and  `quit()` are designed for use in interactive mode.