3次元の回転変換を四元数で記述する方法を紹介します。なお、この内容は先日開催された[第3回すうがく徒のつどい](https://tsudoionline.netlify.app/03/)の「四元数と回転」で話した内容の一部です。その際の[講演資料](https://github.com/usami-k/mathematics/blob/master/2022/QuaternionRotationTsudoi/QuaternionRotationTsudoi.pdf)では計算を省略しましたが、今回は計算も書きます。

## 四元数の定義

&&&def 四元数
$x_0+x_1\ii+x_2\jj+x_3\kk$（$x_i\in\mathbb{R}$）とあらわされる数を、四元数と呼びます。ここで、$\ii$、$\jj$、$\kk$は実数とは異なる数であり、次の関係式を満たすものです。四元数の虚数単位と呼ばれます。
\begin{gather}
    \ii^2=\jj^2=\kk^2=-1\\
    \ii\jj=-\jj\ii=\kk,\quad\jj\kk=-\kk\jj=\ii,\quad\kk\ii=-\ii\kk=\jj
\end{gather}
&&&

四元数の乗法は非可換である点に注意してください。実数と実数の積や実数と虚数との積は可換です。しかし、虚数と虚数の積は可換とは限りません。

四元数$x=x_0+x_1\ii+x_2\jj+x_3\kk$に対して、四元数$\overline{x}$を次で定義し、$x$の共役と呼びます。
\begin{equation}
    \overline{x}:=x_0-x_1\ii-x_2\jj-x_3\kk
\end{equation}

四元数$x=x_0+x_1\ii+x_2\jj+x_3\kk$に対して、実数$|x|$を次で定義し、$x$の大きさと呼びます。
\begin{equation}
    |x|:=\sqrt{x_0^2+x_1^2+x_2^2+x_3^2}
\end{equation}

共役と大きさのあいだに次のような関係があります。これは実際に計算することで分かります。この関係は後で計算に使います。
\begin{equation}
    x\overline{x}=|x|^2
\end{equation}

四元数$x=x_0+x_1\ii+x_2\jj+x_3\kk$と$y=y_0+y_1\ii+y_2\jj+y_3\kk$に対して、実数$\langle x|y\rangle$を次で定義し、$x$と$y$の内積と呼びます。
\begin{equation}
    \langle x|y\rangle:=x_0y_0+x_1y_1+x_2y_2+x_3y_3
\end{equation}

共役と内積のあいだに次のような関係があります。これは実際に計算することで分かります。この関係は後で計算に使います。
\begin{equation}
    x\overline{y}+y\overline{x}=2\langle x|y\rangle
\end{equation}

## 四元数と3次元空間の対応

&&&def 純虚四元数
実部を持たない四元数、すなわち次の形の四元数を純虚四元数と呼びます（$x_i\in\mathbb{R}$）。
\begin{equation}
    x_1\ii+x_2\jj+x_3\kk
\end{equation}
&&&

純虚四元数と3次元ベクトル空間のベクトルを、次のように対応させます。
\begin{equation}
    x_1\ii+x_2\jj+x_3\kk\leftrightarrow(x_1,x_2,x_3)
\end{equation}

純虚四元数$x=x_1\ii+x_2\jj+x_3\kk$と$y=y_1\ii+y_2\jj+y_3\kk$に対して、純虚四元数$x\times y$を次で定義し、$x$と$y$の外積と呼びます。
\begin{equation}
    x\times y:=(x_2y_3-x_3y_2)\ii+(x_3y_1-x_1y_3)\jj+(x_1y_2-x_2y_1)\kk
\end{equation}
これは3次元ベクトル空間の外積と対応しています。

純虚四元数$x$と$y$の積は内積と外積であらわすことができます。これは実際に計算することで分かります。
\begin{equation}
    xy=-\langle x|y\rangle+x\times y
\end{equation}
この関係から次が導けます。これは後で計算に使います。
\begin{equation}
    xy-yx=2(x\times y)
\end{equation}

## 四元数による回転

四元数を使って、3次元空間の回転を次のように記述できます。

&&&thm 四元数による回転
大きさ$1$のベクトル$\vec{n}$があるとします。点$X$を$\vec{n}$の周りに角$\theta$だけ回転した点を$X'$とします。$X$の位置ベクトルに対応する純虚四元数を$x$、$X'$の位置ベクトルに対応する純虚四元数を$x'$とするとき、次が成り立ちます。
\begin{equation}
    x'=qx\overline{q}
\end{equation}
ただし、$q$は次の四元数です（$n$は$\vec{n}$に対応する純虚四元数）。
\begin{equation}
    q=\cos\frac{\theta}{2}+\left(\sin\frac{\theta}{2}\right)n
\end{equation}
&&&

なお、$q$は大きさ$1$の四元数です。実際、$n=n_1\ii+n_2\jj+n_3\kk$とすると、次のようになります。
\begin{align}
    |q| & =\left(\cos\frac{\theta}{2}\right)^2+\left(\sin\frac{\theta}{2}\right)^2(n_1^2+n_2^2+n_3^2) \\
        & =\left(\cos\frac{\theta}{2}\right)^2+\left(\sin\frac{\theta}{2}\right)^2                    \\
        & =1
\end{align}

## ロドリゲスの回転公式への帰着

「四元数による回転」の定理の証明ですが、実は「[ロドリゲスの回転公式](https://mathlog.info/articles/3190)」に帰着できます。

$qx\overline{q}$を計算すると、実は次のようになります。
\begin{equation}
    qx\overline{q}=(\cos\theta)x+(1-\cos\theta)\langle n|x\rangle n+\sin\theta(n\times x)
\end{equation}

この右辺を、四元数と3次元空間の対応を考えてベクトルの記述にすれば次のようになります。
\begin{equation}
    \cos\theta\vec{x}+(1-\cos\theta)\langle\vec{n}|\vec{x}\rangle\vec{n}+\sin\theta(\vec{n}\times\vec{x})
\end{equation}

これは、「ロドリゲスの回転公式」そのものです。したがって、「四元数による回転」の定理が証明できます。

あとは、$qx\overline{q}$の計算結果が確かに上述のとおりであることを示せば証明が完了します。

## 四元数による回転の証明

$q$の実部を$q_0$、虚部（純虚四元数部）を$q_1$とすると、次のように展開できます。
\begin{align}
    qx\overline{q} & =(q_0+q_1)x(q_0-q_1)               \\
                   & =q_0xq_0+(q_1xq_0-q_0xq_1)-q_1xq_1
\end{align}
これを、各項ごとに計算していきます。

$q_0xq_0$の部分は次のようになります。
\begin{align}
    q_0xq_0 & =\left(\cos\frac{\theta}{2}\right)x\left(\cos\frac{\theta}{2}\right) \\
            & =\left(\cos\frac{\theta}{2}\right)^2x
\end{align}

$q_1xq_0-q_0xq_1$の部分は次のように計算できます。
\begin{align}
    q_1xq_0-q_0xq_1 & =q_0(q_1x-xq_1)                                                                                                        \\
                    & =\left(\cos\frac{\theta}{2}\right)\left(\left(\sin\frac{\theta}{2}\right)nx-x\left(\sin\frac{\theta}{2}\right)n\right) \\
                    & =\left(\cos\frac{\theta}{2}\right)\left(\sin\frac{\theta}{2}\right)(nx-xn)                                             \\
                    & =2\left(\cos\frac{\theta}{2}\right)\left(\sin\frac{\theta}{2}\right)(n\times x)                                        \\
                    & =\sin\theta(n\times x)
\end{align}
途中で、純虚四元数の外積の関係式を使いました。また、最後の変形は2倍角の公式$\sin 2\phi=2\cos\phi\sin\phi$を使いました。

$-q_1xq_1$の部分は次のようになります。
\begin{align}
    -q_1xq_1 & =-\left(\sin\frac{\theta}{2}\right)nx\left(\sin\frac{\theta}{2}\right)n \\
             & =-\left(\sin\frac{\theta}{2}\right)^2nxn
\end{align}

ここで、四元数の内積の関係式から次が分かります。
\begin{align}
    2\langle n|x\rangle n & = (n\overline{x}+x\overline{n})n \\
                          & =n\overline{x}n+x\overline{n}n   \\
                          & =-nxn+x|n|^2                     \\
                          & =-nxn+x
\end{align}
ここから、$nxn=x-2\langle n|x\rangle n$が分かります。よって、次のようになります。
\begin{equation}
    -q_1xq_1=-\left(\sin\frac{\theta}{2}\right)^2(x-2\langle n|x\rangle n)
\end{equation}

以上から、$qx\overline{q}$は次のようになります。
\begin{align}
    qx\overline{q} & =q_0xq_0+(q_1xq_0-q_0xq_1)-q_1xq_1                                                                                                                                    \\
                   & =\left(\cos\frac{\theta}{2}\right)^2x+\sin\theta(n\times x)-\left(\sin\frac{\theta}{2}\right)^2(x-2\langle n|x\rangle n)                                              \\
                   & =\left(\left(\cos\frac{\theta}{2}\right)^2-\left(\sin\frac{\theta}{2}\right)^2\right)x+2\left(\sin\frac{\theta}{2}\right)^2\langle n|x\rangle n+\sin\theta(n\times x) \\
                   & =(\cos\theta)x+(1-\cos\theta)\langle n|x\rangle n+\sin\theta(n\times x)
\end{align}
最後の変形は2倍角の公式$\cos 2\phi=(\cos\phi)^2-(\sin\phi)^2$と半角の公式$\left(\sin\frac{\theta}{2}\right)^2=\frac{1-\cos\theta}{2}$を使いました。

これで、無事に四元数による回転の式をロドリゲスの回転公式に帰着させて証明することができました。
