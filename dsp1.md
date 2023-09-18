## Types of systems

Digital systems make use of "discrete time", while analog systems make use of "continuous time".

Discrete time:

> "Discrete time regards the values ​​of a variable as occurring at discrete discrete "points" or as unchanged throughout each non-zero region of equivalent time (a "duration"). That is, time is considered as a discrete variable. Non-time variables therefore jump from one value to another as time moves from one period to the next. This time view corresponds to a digital clock that shows a fixed reading of 10:37 for a while, then jumps to a new fixed reading of 10:38. In this framework, each variable of interest is measured once."

Continuous time:

> In contrast, in continuous time, variables are assumed to have specific values ​​for infinitely short periods of time. Between any two of her points in time there are countless other points in time. The variable "time" ranges over the entire real number line or, depending on the context, over a portion of the real number line, such as a non-negative real number. Therefore, time is considered a continuous variable.

More on the subject [here](https://academic-accelerator.com/encyclopedia/discrete-time-and-continuous-time).

A system either has a:

    finite impulse response (FIR), or an

    infinite impulse response (IIR).

A **finite impulse response** occurs in a system that only processes information in a forward direction, whereas a system with an **infinite impulse response** requires a feedback loop to operate.

In theory, an IIR system will pass a signal indefinitely, gradually diminishing in amplitude. However, in digital systems, this infinitely small value is ultimately rounded down to zero due to the digital limitations in precision, a rounding error essentially

## Comb filters

There are two types of comb filters:

    comb filters with positive feed and

    comb filters with negative feed 

**Comb filters with + feed** produce all of the harmonics, while comb **filters with - feed** only produce odd harmonics that sound an octave lower.

This is the difference between a pipe with a closed and open end, a pipe with a closed end will sound an octave lower. This is used in church organs to get lower octaves without making the pipes too long. 

To make a comb filter, all you need is a delay.

For a delay of 1 millisecond length the frequency 1000 Hz and it's multiples will be amplified. 0 Hz will also always be amplified, it is important to remember that this is not the root note off which the overtones are based.

The simple formula to determine what root frequency will be amplified by a specific delay is:

$$
frequency(kHz) = 1/delay(ms)
$$

If there is a negative feedback coefficient this root frequency turns out of phase, when this happens the root frequency becomes an octave lower and all the odd harmonics become amplified.

An example of such a system is this:

```
             ---------------------
input --+-->| 2 millisecond delay |-->--- output
        ^    ---------------------   |
        |                            |
        * <--------------------------<
        ^
        |
      -0.99
```

In this example you would initially put the delay time in the formula:

$$
1/2ms = 0.5kHz = 500Hz
$$

and you would get 500Hz as a result. Assuming this is the root frequency, the multiples of this frequency would result in the harmonic overtones, namely:

                        1 = 500Hz

                        2 = 1000Hz

                        3 = 1500Hz

                        4 = 2000Hz

                            etc.. 

But note the feedback coefficient which is negative. Because the feedback coefficient is negative the root frequency goes out of phase. 
