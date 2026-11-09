# The Fourier entropy–influence inequality for symmetric Boolean functions

Yitzchak Shmalo

[Paper (PDF)](paper/main.pdf) · [LaTeX source](paper/main.tex) · [Declarations](DECLARATIONS.md)

The paper proves the Fourier entropy–influence inequality for every symmetric Boolean function with constant below 6.1347, improving the constant 12.04 of O'Donnell, Wright and Zhou (ICALP 2011). All logarithms are to base 2, $H(f)$ is the Fourier entropy and $I(f)$ the total influence.

## Main results

- **Theorem A.** Every symmetric Boolean function satisfies

  $$H(f)\le\Bigl(\frac{673}{250}+2+\frac{1}{\ln 2}\Bigr)I(f)=6.1346950408\ldots\,I(f).$$

  The entropy splits into the entropy of the level weights, at most $2.692\,I$ for every Boolean function (Lemma 3.2, which sharpens the bound $\log_2(4+e)\,I$ of Lemma 2.1 of arXiv:2610.16069; its last step is an interval certificate), and a within-level term, bounded here by $(2+1/\ln 2)\,I$.

- **Theorem B.** If $f$ is symmetric on $n\ge2$ variables and $g$ is its derivative in one coordinate, then for $0\le\lambda\le1$

  $$\mathrm{Stab}_\lambda[g]\le e^{-v}I_0(v)\,\|g\|_2^2,\qquad v=\frac{(n-1)(1-\lambda^2)}{4}.$$

- **Theorem C.** For OR and AND, $H/I=4-(4-2/\ln 2)/n+O(2^{-n})$. The optimal constant for symmetric functions lies in $[4,\,6.1347]$.

- **Theorem D.** The entropy cost of restricting one coordinate of a symmetric function satisfies

  $$\limsup_{n\to\infty}\sup_f\frac{\Delta_1(f)}{I_1(f)}<4.637,$$

  so the restriction step with constant 4.8723 can fail in only finitely many dimensions. An explicit cutoff is open.

## Computations

`computations/check_all.py` recomputes the principal constants and the finite computations in the paper and prints PASS or FAIL for each (about ten seconds; needs numpy, scipy and mpmath). It enumerates every symmetric function with $n\le16$: the largest $H/I$ in each dimension is attained by AND and OR, and the largest restriction ratio is $12-\tfrac92\log_2 3=4.8677$ at $\mathrm{OR}_3$. Its output is in `computations/check_all.out`.

`computations/level_entropy_certificate.py` is the outward-rounded interval certificate (mpmath, 45 digits, 7,058 cells) for the one-variable inequality in Lemma 3.2. Its output is in `computations/level_entropy_certificate.json`.

`computations/restriction_majorant_certificate.py` is the outward-rounded interval certificate (mpmath, 45 digits, 11,900 cells) for the pointwise majorant used in Theorem D. Its output is in `computations/majorant_certificate.json`.

```
cd computations
python3 check_all.py
python3 level_entropy_certificate.py
python3 restriction_majorant_certificate.py
```

The paper is part of the Math Brain project, whose public repository is https://github.com/yspennstate/math-brain-public.
