# Jitter of PLL/MMCM output

## Notes

1. When using a PLL to create clocks, it is usually the PLL itself that determines the clock jitter.  That is, jitter for the PLL input clock has little effect on jitter for the PLL 
   output clock.$^{[1]}$

2. In Vivado, we setup the PLL using a Clocking Wizard.  The final tab of the Clocking Wizard tells us the jitter on the PLL output clocks.  Also, the Clocking Wizard tells us 
   that this is Peak-to-Peak (Pk-Pk) jitter (which is about 14 times the RMS jitter).$^{[1]}$

3. In the Timing Report that you show, the Discrete Jitter (DJ) term found under Clock Uncertainty is the Peak-to-Peak jitter for the PLL output clock reported by the Clocking Wizard.$^{[1]}$

4. **Pk-Pk jitter** is a combination of the RMS period-jitter for the clock and a desired value for **Bit-Error-Rate** (BER).  Generally, we use the conversion that Pk-Pk 
   jitter is 14 times the RMS period-jitter which implies a BER of 1 in $10^{12}$.$^{[2]}$

5. There is a maximum input jitter specification for the PLL (< 20% of clock input period or 1 ns, see Table 42 of Xilinx document DS181, DS182 and DS183).$^{[2]}$

6. Generally, if you properly specify external clock jitter to the Clocking Wizard and your project passes timing analysis then the jitter of your external clock is low enough.$^{[2]}$

7. Jitter can be reduced by selecting different options in the Clocking Wizard IP. Output  jitter can be minimized at the expense of input jitter fifiltering. It is recommended to play with these options and evaluate the output under the Port Renaming tab inside the Clocking Wizard . It is possible to improve each path in the design by up to  ±150 ps by selecting optimal settings. Be aware that change in these jitter values could impact power also, because higher frequency of VCO will result in higher power.$^{[4]}$

8. In general, greater jitter filtering is possible by using the MMCM attribute BANDWIDTH set to Low. Setting the BANDWIDTH to low can incur an increase in the static offset of the MMCM.$^{[5]}$

## Reference

1. [How to estimate jitter on output pin?](https://adaptivesupport.amd.com/s/question/0D52E00006hpOgSSAU/how-to-estimate-jitter-on-output-pin?language=en_US)

2. [Clock Jitter for Clock Wizard](https://adaptivesupport.amd.com/s/question/0D52E00006hprNwSAI/clock-jitter-for-clock-wizard?language=en_US)

3. [Specifying a PLL Part 2: Jitter Basics](https://perceptia.com/wp-content/uploads/2021/09/Jitter_Basics_20201009.pdf)

4. [Optimizing Clock Networks to Improve Internal Timing](https://www.fpgakey.com/tutorial/section824)

5. [7 Series FPGAs Clocking Resources User Guide](https://users.ece.utexas.edu/~mcdermot/arch/articles/Zynq/ug472_7Series_Clocking.pdf)
