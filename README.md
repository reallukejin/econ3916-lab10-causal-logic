# econ3916-lab10-causal-logic
# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective
I wanted to see when adding a control variable fixes a biased estimate and when it makes it worse.

## Methodology
- Simulated three worlds: true causation, pure confounding and pure selection, with true effects of 2.0, 0.0 and 0.0
- Drew a confounder, a collider and a mediator as directed graphs with networkx
- Ran regressions with and without a confounder, and with and without a collider, to compare each estimate with the truth
- Built an M-bias structure where the control is measured before treatment
- Wrote a function, coef_on_d(), that returns the treatment coefficient for any list of controls
- Reproduced the LaLonde (1986) contrast, comparing the randomised experiment with a CPS comparison group, then adjusted for covariates

## Key Findings
- The three worlds had correlations of 0.654, 0.664 and 0.632, even though only one had a real effect. The data alone couldn't tell them apart.
- Controlling for the collider gave -0.592 where the truth is 0, a fake effect created by the control itself.
- In the M-bias setup, controlling for W gave -0.197. Also controlling for u1 brought it back to -0.005.
- In the LaLonde data, the experiment gave $1,794 and the naive CPS comparison gave $-8,498. Controls moved it to $699, closing 89% of the gap, but without the experiment I wouldn't have known how close that was.
