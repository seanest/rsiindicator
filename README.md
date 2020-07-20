# rsiindicator
I'm trying to add more time resolutions to standard RSI indictor in TradingView


/@version=4
study(title="Relative Strength Index", shorttitle="RSI", format=format.price, precision=2, resolution="480")
s = input(defval="Current TF Chart", title="custom Session", type=input.string, options=["15", "30", "45", "60", "77", "1D", "Current TF Chart"])
x = iff(s == "Current TF Chart", period, s)
mysession =security(tickerid, x , close)
src =  mysession
up = rma(max(change(src), 0), len)
down = rma(-min(change(src), 0), len)
rsi = down == 0 ? 100 : up == 0 ? 0 : 100 - (100 / (1 + up / down))
plot(rsi, "RSI", color=#8E1599)
band1 = hline(70, "Upper Band", color=#C0C0C0)
band0 = hline(30, "Lower Band", color=#C0C0C0)
fill(band1, band0, color=#9915FF, transp=90, title="Background")


The problem is in tradingview is that implemeting this code I get this error "Script could not be translated from: null" 

any idea how to fix it? 
