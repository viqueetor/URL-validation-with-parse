package main

import (
	"fmt"
	"net"
	"net/url"
)

func UrlIsValid(str string) bool {
	u, err := url.Parse(str)
	return err == nil && u.Scheme == "http" || u.Scheme == "https" || u.Host != ""
	//return err == nil && !parsedurl.IsAbs() || parsedurl.Scheme == "" || parsedurl.Host == ""
}
func main() {
	urls := []string{"https://www.google.com", "https://www.pudim.com", "https://www.stone.co"}

	for _, url := range urls {
		if !UrlIsValid(url) {
			fmt.Printf("A URL %v e invalida\n", url)
		} else {
			fmt.Printf("A URL %v e valida\n", url)
		}
	}
	fmt.Println()

	for _, endpoint := range urls {
		u, err := url.Parse(endpoint)
		if err != nil {
			fmt.Println(err)
		}
		ips, err := net.LookupIP(u.Host)
		if err != nil {
			fmt.Printf("Erro ao resolver o endereço IP da URL %s \n", endpoint)
			fmt.Println(err)
			fmt.Println()
			continue
		}

		for _, ip := range ips {
			fmt.Printf("%s: %s\n", endpoint, ip)
		}
		fmt.Println()

	}

}
